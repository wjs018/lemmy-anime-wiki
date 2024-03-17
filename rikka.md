---
title: Bot User Guide
description: Your guide to rikka, the anime community discussion thread bot.
published: true
date: 2024-03-17T04:44:34.849Z
tags: 
editor: markdown
dateCreated: 2024-03-17T04:44:34.849Z
---

# Your Friendly Neighborhood Bot - rikka

rikka is the name of the bot used to create discussion threads in the anime@ani.social community for currently airing series. Each season, there are ~50 different shows airing, more than our humble little community can handle if each episode that airs is given its own discussion thread. rikka was created to support creating threads just for the shows that the community has demonstrated an interest in.

In this article, I have laid out the different functions of rikka and how you can interact with her to help you discuss the anime that you are interested in.

# How rikka Works

## Before the Season Starts

Prior to the start of the season I, wjs018@ani.social, will create a thread in which users can create a comment mentioning any shows they are planning on watching. I will be manually keeping tabs on this thread and enabling any series that people mention in rikka's database.

## Start of the Season

When the season starts, rikka will create an episode discussion thread for any show that has been enabled in the database. The post will be created once the episode has finished airing (uses the [AniList api](https://anilist.gitbook.io/anilist-apiv2-docs) as a source).

For shows that have not been enabled from the thread before the season, no discussion post will be made. Users are able to request a discussion thread for an episode that doesn't already have one through a pm. See here for details.

## As the Season Progresses

Unlike the first week of the season, the subsequent episode discussion threads are only created if the previous episode's discussion thread has engagement from the community. Specifically, rikka will look at the total number of upvotes and comments on the previous episode's post to determine if there was enough interest to post the next episode. The exact thresholds that a discussion needs to meet will vary for now as the bot is new and I will be closely monitoring the engagement.

The rationale for this engagement criteria is to help weed out shows that the community has stopped watching. It would not be desirable for rikka to continue making discussion posts for a series that no users are watching or engaging with, littering the community with empty posts.

If a show has become disabled through failing to meet the engagement thresholds, but a user still wants a discussion thread for an episode, it can be requested from rikka via pm. See here for details.

## After the Final Episode

Once a show ends, rikka will post an episode discussion thread like normal if the show is still enabled and the penultimate episode meets the engagement thresholds. If the show is disabled or fails to meet the engagement thresholds, then no discussion thread will be created. A user is still able to request a thread be created through pm'ing rikka for some time after the season has ended (see here for details). The exact amount of time after a season ends that a discussion thread can be requested is subject to change, but should be able to accommodate people that are a bit behind the airing episodes just fine.

# Requesting Discussion Threads via PM

If a show is disabled in rikka's database or if the previous episode fails to meet the engagement thresholds, there will not be any discussion thread made for that episode. If a user wants to have a thread to discuss an episode for which a thread wasn't created by rikka, they are able to request an episode be made by private messaging rikka@ani.social.

## Format of the Message

The message to rikka must contain two elements for her to be able to parse it successfully and create the requested discussion thread.

1. The [AniList](https://anilist.co/) link to the show.
2. `Episode XX` where XX is replaced by the episode number being requested.

So, as a hypothetical, if the show Mushishi was currently airing, but no discussion thread was created for episode 3, then you could request one from rikka by messaging the bot with the message:

> https://anilist.co/anime/457/Mushishi/ Episode 3

Something to note is that different seasons will have different AniList pages. So, if you were instead trying to request season 2, episode 3 of Mushishi, the message would need to have the season 2 AniList link:

> https://anilist.co/anime/20595/Mushishi-Zoku-Shou/ Episode 3

Any additional text you provide is simply ignored by rikka. If you were to provide multiple AniList links or episode number phrases, then rikka will just pay attention to the first instance and ignore the rest.

## Response From rikka

rikka will check for new messages every 5 minutes and will reply to your message with a link to the newly created discussion post if everything went well. Alternatively, if there were errors, rikka will reply with some information about what went wrong.

If you think there is an error and that rikka isn't working in a specific case, please reach out to me (wjs018@ani.social). The error information that rikka provides will be helpful for me to figure out any issues that arise.

## Reasons a Thread Cannot Be Created

There are a number of reasons that rikka will refuse to create a discussion thread for an episode other than simply being unable to parse your message:

| Reason | Additional Info |
| ------ | --------------- |
| The show isn't currently airing | Only shows that are currently airing (or recently aired) are able to have episode discussion threads created by rikka. |
| The specified episode has not aired yet | If the show + episode you are requesting has not aired yet (per the AniList api), then rikka will refuse to create the discussion thread. This can be an issue sometimes when different services air the episode at different times. |
| There is a more recent episode discussion thread | If the show you have linked has a discussion thread for a later episode already created by rikka, then she will reject your request. For example, if you request a thread for episode 3, but there is already a discussion thread for episode 5, then rikka will reject this. The intention behind this is to prevent any confusion for users as threads would be made out of chronological order. |
| The show is marked as NSFW by AniList | To make my moderating life easier, I am preventing any shows that are marked as NSFW by AniList from being added to rikka's database. If you want discussion threads about a show that is marked as NSFW, reach out to me directly and I can consider adding that show manually if I think it won't be a headache going forward. |