---
title: AICSImageIO
description: AICSImageIO and the plan to make a comprehensive, scalable, image reading and writing library in pure Python.
date: 2020-09-28
tags:
  - image reading
  - image writing
  - python
  - microscopy
layout: layouts/post.njk
image: /img/aicsimageio/n-dim-render.png
---

![Single cell projections](../../img/aicsimageio/quilt-catalog-cells.png)
<sub>Single cell projections produced from [Automated Cell Toolkit](https://github.com/allencellmodeling/actk).</sub>

This post will be about [AICSImageIO](https://github.com/allencellmodeling/aicsimageio), the work we have already completed, the things coming in the future, and other comments and tidbits along the way. In some ways, this is a rambling version of the ["Mission and Roadmap" documents soon to be added to the AICSImageIO repository](https://github.com/allencellmodeling/aicsimageio/pull/150) so if you prefer to just read those documents, feel free.

##### In Short
AICSImageIO aims to provide a **consistent, intuitive, API for reading in or out-of-memory image pixel data and metadata, regardless of location,** for the many existing proprietary microscopy file formats, and, an **easy-to-use API for converting from proprietary file formats to an open, common, standard** -- all using either language agnostic or pure Python tooling.

##### Background
When I first started at Allen Cell, I was immediately tossed into reading and writing multi-dimensional volumetric image data -- something I had no prior experience in doing. Image manipulation in programming made _decent_ sense to me in terms of n-dimensional array manipulation, but, I didn't have any idea of the current problems in scalable, robust, and unified image reading and writing.

Prior to Allen Cell, the largest images I had ever interacted with in-memory in programming were _small_ -- a couple of MBs perhaps and all either 2D or 2D RGB (3D). What I would soon learn was that images can get _large_. Really large. On average, the microscopy images that Allen Cell works with are about 400 MBs in size and I think the most common array shape I interacted with was around (7, 75, 624, 924) -- 7 channel, 75 Z-stack images. These are large images when compared to what most people interact with on a daily basis but these weren't even close to the upper bound of the sizes of images we could possibly produce, and, most importantly, these images can fit into most workstation's memory. Notably, there was no time-series data in the above "most common" example, in the time-series case for Allen Cell, our files commonly were much larger, usually somewhere in the multi-GB range -- the largest I have seen was 200GB.

![An image of a cell rendered in napari](../../img/aicsimageio/n-dim-render.png)
<sub>A three dimensional (ZYX) image of a cell rendered with <a href="https://napari.org">napari</a> with structure, membrane, and DNA channels visible.</sub>

Images at Allen also come in a few formats, from proprietary file formats such as `CZI` and `LIF`, to open standards like `OME-TIFF` with each format containing their own metadata schema. This is incredibly important because while the underlying image pixel data is generally all the same structure -- "a bunch of YX planes in some shape or another", the metadata schemas can vary widely and contains important pieces of information such as the channel names, the pixel size, the acquisition setup, etc.

So what do you do when you have a scientist who wants to port some analysis code from using one image dataset to another, but, they have a couple of issues:

* the original dataset they used their analysis code against was written for reading and interacting with the metadata of a different file format
* the original dataset contained files that were much smaller -- usually this is because they were using a small scale sample

##### Too Many Formats
Let's start by addressing how to create a "scalable" image reading library. Generally, when people talk about the "scalability" of something in programming they are referring to how well a program or infrastructure can handle more and more load, users, requests, etc. But, in the case of AICSImageIO, we use this term to mean:

> How easy is it to add support for reading a new proprietary file format?

There are a couple of things to unpack here:

* How "easy" something is is a bad way to say "how well does the developer specification allow for 'my new cool custom image file format'."
* Notice, we only mention "reading" a new file format, not writing. We are pretty set on this as we want to "encourage" that the easiest way to share data with others is with a single image writer to common standards.

As previously mentioned, regardless of file format, _most_ file formats store image pixel data relatively the same -- "a bunch of YX planes in some shape or another," and generally, when adding support for a new file format to the library we wanted to make that as easy as possible.

> If you provide this image Reader object with a method to read a buffer and return an n-dimensional array with the dimension short-names, we're good.

This is similar to how other libraries have done it as well (i.e. [imageio](https://github.com/imageio/imageio)). Where we differ however is in handling of metadata. It is hard to talk about which pieces of metadata are "the most useful" as everyone has different needs, but there are a few standouts: channels names, pixel size, dimension order and names, etc.

I _personally_ think:

> the pieces of metadata that are most useful to computational scientists are those which enable the scientist to complete their work without ever having to _view_ the file.

<sub>A disclaimer, I will always recommend viewing a sample of the images in a dataset regardless however to make sure that your programmatic understanding of the images you are operating on match your biological understanding.</sub>

In this way, we, the developers of AICSImageIO should try to enable access to the pieces of metadata that are most common _across_ file formats, _and_, allow for rapid development without having to constantly open and view different images.

So, in adding a file format to the library, _sure_, you can just add a Reader that will return the user "just the pixel data" but you should also find a way to read and parse the valuable bits of metadata.

##### Delayed Image Reading
So great, we can scale and add readers to the library, and we can enforce that those image readers also read and parse the valuable bits of metadata. What happens when we scale to a multi-hundred GB image? How does the Reader interface change?

Fortunately for us, there are much smarter people out there that have already worked on "delayed / distributed array handling problems" for much longer than I have and in general, the problem of reading an image into memory is quite similar to creating a delayed array for that same image.

To expand our image reading specification, we simply added a requirement to image readers that requires that they must contain both a function to read the image into memory just like before, but also a function to read YX planes on request (or whatever chunk size they want).

There has been some difficulty getting these delayed arrays to operate exactly as intended, and largely this has admittedly been my over-promising of their value in all situations, but, this does work well as a solution for expanding the API to have both in-memory and out-of-memory data have the same functional interface.

##### Where To Go
One of the problems of development on libraries like this that I have found is that once we made AICSImageIO 3.0 stable, we had to split our time between fixing user reported bugs, minor reworks to optimize behavior, and etc, versus simply continuing on with the high level goals. That isn't to take away from those activities as they are drastically important in shaping future work as well, it is simply that I have this excitement of adding _even more_ value to the library, to show what all is possible with even more work but keep having to reign that excitement in (just a bit).

Again, in my opinion, the high level goal of AICSImageIO is to:

> provide a **consistent, intuitive, API for reading in or out-of-memory image pixel data and metadata, regardless of location,** for the many existing proprietary microscopy file formats, and, an **easy-to-use API for converting from proprietary file formats to an open, common, standard** -- all using either language agnostic or pure Python tooling.

So we are actively working on adding support for `fsspec` (Filesystem Specification), a Python library that allows for path like handling of local or remote file systems.

We are cleaning up our API even further to have a standard for function and property naming and convention.

We are standardizing our Reader expansion further to allow for even more general, and safe, image reading with better scene management.

And the one that gets me most excited is our work on language agnostic metadata conversion. If we want to have a unified API for metadata access and interaction, well, it would be great that if instead of "emulating" the open standard if we just converted straight to the open standard. Many projects have already done parts of this work but are baked into the library itself, in a programming language, and we want to expand on their existing work by making their, and our work, converting between metadata schemas language agnostic so it can be imported and used in any language. (See the [OME](https://www.openmicroscopy.org/) and [bioformats](https://github.com/ome/bioformats) teams and projects)

Lastly, one of the other benefits of writing this library in pure Python is the ability to interact with the other existing Python ecosystem. We were one of the first teams to add an image reading plugin to [napari](https://napari.org), but, we hope to also make an image writing plugin after finishing our 4.0 series of changes, thus enabling a **single** library to manage the reading and writing of image data for both computational and non-computational users in pure Python.

![A full view of the napari viewer of the previous n-dimensional image render](../../img/aicsimageio/napari-example.png)
<sub>A full view of the napari viewer rendering a three dimensional (ZYX) image of a cell rendered with <a href="https://napari.org">napari</a> with structure, membrane, and DNA channels visible made possible by directly reading an image with the `napari-aicsimageio` plugin.</sub>
