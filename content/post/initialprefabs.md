---
title: "InitialPrefabs"
date: 2021-10-18
draft: false
pinned: true
tags:
  - work

summary: "The consulting work I do at initialPrefabs"
---

I founded my own game development consulting company, [initialPrefabs](https://initialprefabs.com) 
around June of 2016 with my brother. 

I primarily focus on building custom tools for game developers and optimizations for mobile, 
desktops, and VR. Some studios I have worked with include:

* [The Feast](#the-feast)
* [Computer Lunch](#computerlunch)
* [ESC Game Theater(Defunct)](#escgametheater)
* [Metamorphasis Games](#metagames)
* [Metis Suns](#metissuns)
* [Mokuni LLC](#mokuni)
* [Unity Technologies](#unity)
* [vrWiz](#vrwiz)
* [Whalefood Games](#whalefoodgames)

## The Feast {#the-feast}
[![The Feast](https://img.youtube.com/vi/5E8Hh8P0HCE/maxresdefault.jpg)](https://www.youtube.com/watch?v=5E8Hh8P0HCE "The Feast")

The Feast, is a rogue like developed by Tim Conkling (creator of [AntiHero](https://antihero-game.com/)). On this 
project, I was primarily responsible for helping the team migrate from a Forward renderer to a custom deferred 
renderer with custom cell shading. **Click the banner for a link to the in game trailer!**

This meant overriding Unity's default deferred pipeline in URP and encoding the correct data to the GBuffers as 
well as support common features found in URP such as Light Layers, dynamic occlusion culling, integration of a custom
deferred pipeline in artist friendly tools such as ShaderGraph and Amplify.

Additionally, I developed a procedural lantern spot light system, that dynamically scales to the surface it's pointed to, mimicing
volumetric lights.

## Computer Lunch {#computerlunch}
### Cell to Singularity

![banner](https://www.celltosingularity.com/img/cell_to_singularity_app_icon.png)

Cell to Singularity is an educational clicker idle game, where I was contracted to help Computer 
Lunch develop a feasible save system in their existing architecture. This was to help delay and 
potentially prevent users from editing their save file which may allow them to cheat and gain 
tons of resources. Simultaneously, this was used as the backbone for the team's cloud saving 
architecture, as save data was stamped and signed allowing for easy version control.

For more information on where you can grab Cell To Singularity, please see [here](https://www.celltosingularity.com/).

## ESC Game Theater(Defunct){#escgametheater}

Well ESC Game Theater is now defunct and I imagine assets have been liquidated by their parent 
company, [ESI Design](https://esidesign.nbbj.com/). Because of that I can't link any work I have 
done for them as none of their links work anymore. 

In order to help support them in building interactive jumbotron experiences, I worked on 
helping them optimize rendering in WebGL by creating a custom rendering pass which allows 
all elements be draw efficiently in 1 draw call.

## Metamorphosis Games{#metagames}
### Gestalt Steam & Cinder{#gestalt}

![banner](https://cdn.akamai.steamstatic.com/steam/apps/1231990/header.jpg?t=1629970667)

In 2018, I was contracted to help Metamorphosis Games build Gestalt: Steam & Cinder. Here I was 
responsible for developing hierarchical state machines (HSM) for many of the grunt enemies in their 
games, developing and finetuning a generic cross fade animation system for responsive controls 
for all characters, and built editor tools such that the game designers can tweak paramteres easily 
without having to touch the codebase.

[Steam](https://store.steampowered.com/agecheck/app/1231990/)

## Mokuni Games {#mokuni}
### Kitty in the Box 2 (Released, Mobile){#kitty-in-the-box}

![banner](http://mokuni.com/press/Kitty%20in%20the%20Box%202/images/header.png)

Kitty in the Box 2 is a mobile game where you aid, Sushi our lovable cat, jump into boxes. The game 
is released for Android and iOS in 2017.

* [Android](https://play.google.com/store/apps/details?id=com.mokuni.kib2&hl=en_US)
* [iOS](https://apps.apple.com/us/app/kitty-in-the-box-2/id1106313526)
* [Presskit](http://mokuni.com/press/sheet.php?p=Kitty%20in%20the%20Box%202)


## Kitty in the Box VR{#kittyvr}

![banner](http://mokuni.com/press/Kitty%20in%20the%20Box%20VR/images/header.png)

Kitty in the Box VR originally started as marketing material for Kitty in the Box 2. Eventually, 
the folks at Mokuni Games found inspiration to turn it into a game and so I started transitioning 
from prototyping work in VR into creating the backbone infrastructure to allow users to interact 
with Sushi. 

This included 
* developing custom modes for the HTC Vive Controller
* developing the force & penetration system to ensure that players would not stab their hands 
into Sushi 
* developed an efficient navigation sampling system so that Sushi can navigate on 
procedurally generated levels

Unfortunately, the project is now defunct and the game was never released.

[Link](http://mokuni.com/press/sheet.php?p=Kitty%20in%20the%20Box%20VR)

## Metis Suns {#metissuns}

### Emissary the Sunsets the Self (Released)

![banner](https://d2w9rnfcy7mm78.cloudfront.net/2455622/display_c572f2f995faf7d9d8ceb3b7e6749739.png)

Emissary the Sunsets the Self is the final episode in Ian Cheng's Emissary's trilogy, which follows 
a civilization's relationship with a sentient slime like creature. The episode was built in Unity 
where I primarily worked on developing a graph based node editor which allowed Ian to 
craft utility theory based AI that fit his design needs.

The project was first released and shown at Museum of Modern Art in 2017.
* [Link](http://iancheng.com/emissaries)

### Bag of Beliefs (Released)

![banner](https://d2w9rnfcy7mm78.cloudfront.net/2663713/original_5961e121e6b2cc91b90ce77bda1563f8.jpg)

Bag of Beliefs is another art exhibit and game, where attendees can interact with a sentient create 
called BOB. BOB uses exhibit provided phones to allow attendees to interact with it in order to receive 
acceleromter and motion data and determine how the attendede is interactign with it. I worked on 
optimizing the runtime and building the infrastructure to enable teammates to focus on building 
BOB's AI.

Tools I built included
* Shader visualization system to easily debug the state of BoB's nodes
* Force normalization and dampening to ensure that BoB's nodes did not violently react to extremities 
in impulse applied by exhibit attendees
* integration with proprietary NLP software such that BoB actually understood different commands

The project was first released and shown at the Gladstone Gallery in 2018.
* [Link](http://iancheng.com/BOB)

## Unity Technologies {#unity}
### Kart Microgame (Released)

![banner](https://assetstorev1-prd-cdn.unity3d.com/key-image/1c64e0ff-1b57-48ad-8b3d-ab7bf63e6d0c.webp)

Kart Microgame is Unity's beginner template for an arcade racing game. I helped developed this for 
Unity via Thousand Ant in order to bring gameplay updates to the kart vehicle physics, provide the 
initial ML Agents template for new users, and to optimize the game for mobile WebGL.

The project was officially upgraded at the end of 2019.

Please view the associated video [here](../thousand-ant).

## vrWiz {#vrwiz}

### Inwards VR{#inwards}

![banner](https://static.wixstatic.com/media/7e1185_7e2d1afe25994e019c616392d5f72a41~mv2.jpg/v1/fill/w_1956,h_1108,al_c,q_90,usm_0.66_1.00_0.01/Screen%2520Shot%25202021-03-12%2520at%252015_42_.webp)

Inwards is a VR game about exploring your choices. Most of my work with Inwards involve creating custom 
workflow tools for teammates and optimizing the current rendering stack in order to improve performance.

This allowed the team to push the rendering limitations of their game on the Oculus Quest (v1).

[Link](https://www.vrwiz.co/projects)

## Kung Fu Kickball (Released) {#whalefoodgames}

![banner](https://www.kungfukickball.com/images/Screenshot1.png)

Kung Fu Kickball is a multiplayer fighting sports game where the goal is to score the most points 
by kicking the ball into your goal. In order to help Whalefood Games potentially compensate for a 
lack of players online, I helped them train an agent to introduce competitive bots instead of 
building a classical experts based AI system (State Machine/Decision Trees). 

The research to train the AI was primarily based on the following [paper](https://arxiv.org/pdf/1702.06230.pdf).

Kung Fu Kickball is recently [released as of 2021](https://store.steampowered.com/app/1004620/KungFu_Kickball/).
