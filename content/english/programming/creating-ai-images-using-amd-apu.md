---
title: "Creating AI images using AMD integrated graphics card (APU)"
date: 2024-08-09T13:09:25+04:00
tags:
  - AI
---

{{< figure src="/images/programming/creating-ai-images/webui.webp" >}}

## Contents

* [Introduction]({{< relref "creating-ai-images-using-amd-apu.md#introduction" >}})
* [System requirements]({{< relref "creating-ai-images-using-amd-apu.md#system-requirements" >}})
* [Stable diffusion installation]({{< relref "creating-ai-images-using-amd-apu.md#stable-diffusion-installation" >}})
* [Increasing GTT memory size]({{< relref "creating-ai-images-using-amd-apu.md#increasing-gtt-memory-size" >}})
* [Generating images]({{< relref "creating-ai-images-using-amd-apu.md#generating-images" >}})

## Introduction

Many people believe that generating images requires significant computing power and the latest graphics cards. While
this is partly true, and many opt for cloud solutions, **it's actually possible to create basic images locally on your
computer with just an APU** (a processor with an integrated graphics).

On July 14, the new Linux kernel 6.10 was released, bringing an important update: ROCm now supports not only VRAM [but
also allocations in the GTT domain](https://www.phoronix.com/news/Linux-6.10-AMDKFD-Small-APUs). Previously, you had to
adjust VRAM settings in the BIOS, and some BIOS versions
limited VRAM allocation to 2 or 4 GB (which is extremely insufficient for generation tasks).
With kernel 6.10, you no longer need to make these adjustments in the BIOS, as ROCm can now handle allocations in the
GTT domain directly, making the process much more convenient.

This article will cover the steps to deploy a stable diffusion generative AI model locally, using
[AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui).

## System requirements:

- **Linux** (with kernel 6.10+)
- **Arch/Manjaro** (not necessarily arch-based, but in the article the author will use Manjaro)
- At least **16 GB of RAM**
- **AMD APU** (the author will use Ryzen 5 4600G)

## Stable diffusion installation

First you need to install the necessary packages:

1. Let's start with Python 3.10. Note that Manjaro uses the new version
   3.12, however we can still install Python 3.10 via AUR:

{{< highlight bash >}}
pamac install python310 # if you are using arch you can use 'yay'
{{< / highlight >}}

2. The next step is to install *python-pip*:

{{< highlight bash >}}
sudo pacman -S python-pip
{{< / highlight >}}

3. Now we can install pytorch with ROCm backend:

{{< highlight bash >}}
sudo pacman -S python-pytorch-opt-rocm
{{< / highlight >}}

4. Install torchvision with ROCm backend using AUR:

{{< highlight bash >}}
pamac install python-torchvision-rocm
{{< / highlight >}}

5. Clone [stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) repo and setup venv
   environment

{{< highlight bash >}}
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui

python3.10 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
{{< / highlight >}}

6. **Launch**. Run the following inside the project root to start webui:

{{< highlight bash >}}
source venv/bin/activate
./webui.sh --precision full --no-half --lowvram
{{< / highlight >}}

At this stage you should have a working stable diffusion webui.
You can enjoy it now.

If you encounter any problem, please review [the wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki).

## Increasing GTT memory size

As already mentioned, integrated graphics uses system memory, in particular it can use GTT memory, which has
a [default value](https://www.kernel.org/doc/html/v4.19/gpu/amdgpu.html).
But you can increase it! This is something that cannot be done with dedicated graphics cards!

To change the GTT size we need to change the module parameters (amdgpu).
The easiest way is to edit boot loader configuration **/etc/default/grub**:
{{< highlight bash >}}
sudo nvim /etc/default/grub
{{< / highlight >}}

Find the line **GRUB_CMDLINE_LINUX_DEFAULT="..."**
and add **amdgpu.gttsize=102440** (here I allocated 10 GB, you can allocate any other reasonable amount).

Simplified example:

{{< highlight lua "linenos=inline,hl_lines=6">}}

# GRUB boot loader configuration

GRUB_DEFAULT=saved
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR="Manjaro"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amdgpu.gttsize=10240"
{{< / highlight >}}

Keep in mind that GTT, unlike VRAM, can be used by both the system and the integrated graphics.

Now update the GRUB configuration and restart:

{{< highlight bash>}}
sudo update-grub
reboot
{{< / highlight >}}


To check the allocated GTT memory, use the command:
{{< highlight bash>}}
sudo dmesg | grep 'amdgpu.*memory*'
{{< / highlight >}}

You'll get something like this:

{{< figure src="/images/programming/creating-ai-images/gtt.webp" >}}

## Generating images

In this part we will generate a cat 🐈‍⬛ using
the [Vixon's Fantasy Mix](https://civitai.com/models/234898/vixons-fantasy-mix)
model.
Upload your models (checkpoints) to the folder "stable-diffusion-webui/models/Stable-diffusion".
Keep in mind that not every model may work with your APU.

Set seed to 642323556011352 and CFG Scale to 4.5.

Use the following prompt:
> black fluffy gorgeous dangerous cat animal creature, large orange eyes, big fluffy ears, piercing gaze, full moon,
> dark
> ambiance, best quality, extremely detailed

Negative prompt:
> worst, artifacts, deformed, distorted



{{< figure title="GTT memory load during image generation (via radeontop)" alt="GTT memory load during image generation"
src="/images/programming/creating-ai-images/radeontop.webp" >}}

Finally, you will get something like this:

{{< figure title="Final result" alt="Generated image" src="/images/programming/creating-ai-images/webui.webp" >}}

This way we were able to install stable-diffusion-webui and run it locally on the APU, without a graphics card (and
generate a cat).

Of course, generation will be easier and much faster using the
new [AMD Ryzen 8000G Series processors](https://www.amd.com/en/partner/articles/ryzen-8000G-series-processors.html),
which are NPUs.
However, as we have already learned, for owners of 4000 and 5000G series processors, it is possible to use AI models
using an iGPU.
