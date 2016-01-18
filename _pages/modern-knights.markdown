---
layout: page
title: Modern Knights
permalink: modern-knights
---

## What is Modern Knights?

Modern Knights is a strategy/FPS single player game, where the goal of the player is to liberate a city from medieval knights. The inspiration grew from the "prequel" to the game, A Knight in the Park, but instead of having a simple survival game, my team and I wanted to expand the gameplay and test a plugin we were developing on the sidelines.

## Game Phases

The gameplay is essentially split between two phases, I'll dub them as "Planning Phase" and "Action Phase." 

### Planning Phase

The planning phase is essentially the stage where the player prepares his/her loadout and is able to "upgrade" equipment. 

The loadout generally includes a set of ranged weapons (guns) and each weapon has a set of skills. The reason for this is that I wanted to define each weapon to be unique. For example, a revolver is primarily associated with the wild west and in many shows or movies, they're involved in revolver duels (quickdrawing!). Thus one aspect of a revolver is to benefit the player's/weapon's abilities when switching over to use a revolver.

### Action Phase
The action phase is essentially the phase where the player is drawn into battle. The player controls a first person controller whose goal is to capture a series of bases and connect them together. When a link is formed from the player's main camp to the enemy's main camp then the player wins the stage. If a link is formed from the enemy main camp to the player's main camp, then the player loses the level, as knights have taken over the entire district.

Each Action Phase begins with the player and the enemy only owning one base. Each side rushes to capture and gain as many bases as they can before both factions actually contact each other. As soon as contact is met between both factions, then the enemy's objective is to eliminate the player. If the player dies, then the level is lost.

## Why build this game?

Well, aside from merging two different kinds of gameplays and styles together, this game is rather AI heavy. The medieval knights are clearly outgunned (swords and bows vs modern guns), so in order to compensate they'll need both numbers and tactics. While trees and state machines might work for the game, we wanted something more dynamic that mimics a person who is competent on the battlefield.

So introduce a neural network AI System. Since information is constantly being evaluated rather than doing constant condition checks, pick the task that best fits the situation! So in a way, Modern Knights serves as a public testing ground for our custom AI system.
