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
### Low priority tasks
- [ ] Fix chroma key so clips are cut out more cleanly (green fill in instead of black?)

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
- Snippets are short 3-8 second video clips, captured and stored as discrete video files, encoded with HAP.

### On creating a live compositing interface with hand gestures (pinch + translate, scale, rotate)

**Notes:** 
Order of operations in performance is important here, since using hand tracking to composite will require that I go up close to the camera for my hands to become legible. Alternatively, I could use my entire body, selecting with pose, and using body gestures (hand proximity for scale, midpoint between hands for position, hands rotating for rotation.) The hard part with that is that I need some way to select and de-select clips without messing up the positioning I've done. I think for now, the strategy is to build with my hands in mind (it's okay if in this version I have to walk up close to the camera.) Actually, I do have two of those clickers, I could use one of them for select/deselect if I'm using my whole body. But yeah, for now, let's build around using my hands, even though I think that the whole body as controller will be more interesting and work better conceptually. Using the hands is a bit too "interface-y"


- [ ] Figure out which clip I'm selecting (Render Pick)
- [ ] Select with left hand, maneuver with right hand?
- [ ] 

#### Wireless button info
(I just ordered a remote camera shutter button (https://www.amazon.com/ATUMTEK-Smartphones-Wireless-Bluetooth-Included/dp/B0DBVKT3QS?sr=8-17)) so we'll see how that works ([Gemini convo about this](https://share.gemini.google/ATxUs89sMGk3))
> The "Hacked" Smartphone Camera Remote ($5 - $7)
> You can buy simple, generic Bluetooth shutter remotes online or at a local electronics shop for just a few dollars. They are incredibly lightweight, run on a coin cell battery, and often come with a small wrist strap loop.
>  **How it works:** When you pair this cheap remote to your PC, it doesn't send a specialized MIDI or OSC signal. Instead, it literally mimics a standard Bluetooth keyboard and "types" a specific key—usually **Volume Up** or **Enter**—because that is what triggers a phone camera app.
>  **How to link it to TouchDesigner:** 1. Pair the remote to your laptop via standard Bluetooth settings. 2. Open your TouchDesigner network and drop down a **Keyboard In DAT**. 3. Watch the DAT when you press the remote button to see which key it registers (it will likely be `volume_up` or `enter`). 4. Attach a **DAT to CHOP** or write a simple script inside the Keyboard In DAT's callbacks to pulse your effect switch whenever that specific key name is registered.
>  **Pros:** Unbeatably cheap, incredibly light, and zero code or hardware modification required.


## Stopping Note

2026.07.10, 8:40pm
**Summary**
Got the drag and drop working. still need to implement scale, rotation. Currently stuck trying to install voice transcription stuff. the wifi

---

2026.07.09, 9:20pm
**Summary**
Wow, 3D render picking, what a headache! After some annoying (but ultimately educational) detours thanks to gemini, i managed to finally get the render pick with mediapipe to work. Essentially, the midpoint between my index finger and thumb successfully identifies which clip it is hovering over. I have more to say about this later, and I'd like to go back and study this 3D rendering stuff a bit more but I learned quite a lot (I think?) **But wow, it sure feels amazing to see the Render Pick DAT correctly show which clip i'm hovering over.**

**Pick up here**
Well, there is still much to do, but the rest kind of feels like managing a bunch of systems and making sure things happen in the order they need to. For now, I need to implement the select-->drag and drop-->deselect flow. And then, well...then I have to kind of do all of that with the AI. Just some quick musing, I think that maybe when a clip is selected, it is automatically sent via NDI over to the AI, which has its own separate controls on that machine. **I think that for each clip being passed through, I need to swap in the AI version before the Trace happens. Hopefully keeping the diffusion steps all the way down (and thus preserving the original images), will result in the same traced mask so that i can do a nice fade between the original image and the AI.**

---

2026.07.08, 3:50p
**Summary**
Well, it took a while to get my PC at home back up and running. I had to re-install a bunch of things, so I didn't have as much time to work today as I had planned. I also got stuck with dealing with a rather important issue, which was z-fighting with the clips. With Gemini's help ([link to convo](https://share.gemini.google/1TbzBQSzWlbJ)), I was able to solve that problem! I have a bunch of clips all occupying their own slice on the z-axis, with transparency.

**Pick up here**
Now, I need to actually implement the render pick to make sure that I can grab the clips. I still need to figure out the best way to do this (hands, body), but I think I'll begin by testing with the mouse. I also want that "bring to front" feature that gemini suggested. Then...i have to figure out when and how to do the AI stuff. One clip at a time vs. the entire composition all at once...

---

2026.07.08, 5:00pm

My clip bank is working (in 3D space!) today was a bit annoying in dealing with configuring software environments. in a lot of ways it was jogging in place—setting up background removal with the native nvidia background app (and downloading the SDKs for that)...then getting hand tracking at the very least *into the network.* all told though, i spent a good deal of time just futzing with getting synology drive to sync so i could move files between systems. it's a bit clunky, but it mostly seems to be working. **when i continue, i need to keep working on the clip creation and selection in 3d space**

---

2026.07.04, 6:30pm

My clip bank is working! it currently uses a MIDI controller to capture a clip, but this can be handled with any kind of button press. I also created a "clear all" button to dump old clips, which will come in handy later. That was quite finnicky. Next, I need to figure out how to SELECT the snippet I want (both in terms of how I want to do that in the performance, and how to implement that technically), and then I need to map that to gesture controls. After that, i'll have to figure out how that's supposed to go in the AI. (Pick up with this gemini conversation: [TouchDesigner Recording: Ram vs Disk](https://share.gemini.google/L0y3hUudbSP5))