---
title: Bloom Live
type:
  - artwork
status: active
started: 2026-07-02
publish: false
---

# Bloom Live (working title)

## What I'm Making

A series of performances that use real-time AI image generation to create "video compositions" based on using my body as input imagery, and live compositing capture snippets of my body into a single canvas. This more or less builds on Bloom (a video piece) as a proof of concept. Ideally, the performances will culminate in these looping video compositions that will become artifacts in a video installation

## Components
(List any sub-projects or related outputs as links)
- [[Bloom Live sketch]]

## Tasks
- [x] Create module for capturing short video snippets live
	- [x] Add clear all feature
- [ ] Configure MediaPipe Hand detection for selecting and placing clips in composition
- [x] Convert clip generation to happen in 3D space
	- [ ] Set up Render Pick for selecting individual clips in 3D space
- [x] Test NDI for sending video back and forth between PCs
- [x] Install and test StreamDiffusion on PC2
- [ ] Configure Speech-to-text live transcription with local models in TD
	- [ ] voice transcript to prompt pipeline
- [ ] Pipeline for sending clips over to StreamDiffusion

## Technical Info

### Software
- TouchDesigner 2025
- To use Nvidia TOPs in TD, download Video Effects SDK from here: https://www.nvidia.com/en-us/geforce/broadcasting/broadcast-sdk/resources/
- Remap the camera shutter button to keyboard key that can be read by TD using **Powertoys** (default for shutter button is Volume Up...currently remapped to 0)
- [StreamDiffusionTD 0.3.1](https://dotsimulate.com/docs/streamdiffusiontd) by DotSimulate for real-time AI video in TouchDesigner
	- SDXL-Turbo for images
	- Using Cuda 12.8, Python 3.11.9
- LiveTranscribe 0.1.8 by DotSimulate for real-time local voice transcription?

### Hardware
- Primary PC: Intel i9 12900K, RTX 4070Ti Super (16GB VRAM), 32GB RAM
- Secondary PC (AI Video): Intel i9 14900K, RTX 4090 (24GB VRAM), 32GB RAM
- Amutek bluetooth smartphone camera shutter button
- DJI bluetooth lavalier microphone

## Key Sources and Notes

I have a bunch of modules I need to build in TouchDesigner, and things I need to figure out.

- [ ] speech to text (local?)
- [ ] capture and store a snippet of live video
	- [ ] store a bank of snippets
- [ ] mediapipe gestures for mode switching
- [x] send media back and forth across the network (NDI?)
- [ ] use pos, pinch and rotation to position and place snippets

### On capturing and storing a bank of snippets

In this performance, I need to be able to start and stop the capture of a snippet. This might benefit from a button...

So assuming a button toggle to start and stop a snippet recording, what needs to happen?

1. Press Button (Start Recording)
2. Perform gesture (2-5 seconds...so 60-150 frames).
3. Press button (stop recording)
4. A snippet is created!
5. The snippet needs to be played back in real-time (30fps)

it seems like the best way to do this is by recording short HAP videos and then loading/playing back, instead of using cache or tex3d arrays. I'm going to try to set up the dynamic capture system with Gemini's suggestion [gemini convo](https://share.gemini.google/cWApPVDsTUGT)

Ok, so I have a makeshift clip recorder created. that took a little while, but yeah. now i need to build out the replicator and file manager to dynamically load and composite all of these clips

#### What is a snippet?

~~- frames are fed from an input source to a **tex3d array**
	- the number of frames stored depends on the **cache size** parameter, where the value denotes number of frames
	- if i'm capturing gestures on the fly, the cache size needs to be flexible and adapt based on the number of recorded frames~~
- Snippets

#### Wireless button info
(I just ordered a remote camera shutter button (https://www.amazon.com/ATUMTEK-Smartphones-Wireless-Bluetooth-Included/dp/B0DBVKT3QS?sr=8-17)) so we'll see how that works ([Gemini convo about this](https://share.gemini.google/ATxUs89sMGk3))
> The "Hacked" Smartphone Camera Remote ($5 - $7)
> You can buy simple, generic Bluetooth shutter remotes online or at a local electronics shop for just a few dollars. They are incredibly lightweight, run on a coin cell battery, and often come with a small wrist strap loop.
>  **How it works:** When you pair this cheap remote to your PC, it doesn't send a specialized MIDI or OSC signal. Instead, it literally mimics a standard Bluetooth keyboard and "types" a specific key—usually **Volume Up** or **Enter**—because that is what triggers a phone camera app.
>  **How to link it to TouchDesigner:** 1. Pair the remote to your laptop via standard Bluetooth settings. 2. Open your TouchDesigner network and drop down a **Keyboard In DAT**. 3. Watch the DAT when you press the remote button to see which key it registers (it will likely be `volume_up` or `enter`). 4. Attach a **DAT to CHOP** or write a simple script inside the Keyboard In DAT's callbacks to pulse your effect switch whenever that specific key name is registered.
>  **Pros:** Unbeatably cheap, incredibly light, and zero code or hardware modification required.


## Stopping Note

My clip bank is working (in 3D space!) today was a bit annoying in dealing with configuring software environments. in a lot of ways it was jogging in place—setting up background removal with the native nvidia background app (and downloading the SDKs for that)...then getting hand tracking at the very least *into the network.* all told though, i spent a good deal of time just futzing with getting synology drive to sync so i could move files between systems. it's a bit clunky, but it mostly seems to be working. **when i continue, i need to keep working on the clip creation and selection in 3d space**

---

My clip bank is working! it currently uses a MIDI controller to capture a clip, but this can be handled with any kind of button press. I also created a "clear all" button to dump old clips, which will come in handy later. That was quite finnicky. Next, I need to figure out how to SELECT the snippet I want (both in terms of how I want to do that in the performance, and how to implement that technically), and then I need to map that to gesture controls. After that, i'll have to figure out how that's supposed to go in the AI. (Pick up with this gemini conversation: [TouchDesigner Recording: Ram vs Disk](https://share.gemini.google/L0y3hUudbSP5))