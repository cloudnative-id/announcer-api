---
title: Announcer API Scope and Objectives
authors:
  - "@girikuncoro"
reviewers:
  - "@zufardhiyaulhaq"
  - "@2pai"
creation-date: 2020-01-14
last-updated: 2020-01-14
---
# Announcer API Scope and Objectives

This is a living document that is refined over time. It serves as guard rails for what is in and out of scope for Announcer API. As new ideas or designs take shape over time, this document can and should be updated.

## Table of Contents

* [Statement and Objectives](#announcer-api-statement-and-objectives)
  * [Metadata](#metadata)
  * [Table of Contents](#table-of-contents)
  * [Summary](#summary)
  * [Glossary](#glossary)
  * [Motivation](#motivation)
    * [Goals](#goals)
    * [Non\-goals](#non-goals)
  * [Requirements](#requirements)
  * [Workstreams](#workstreams)

## Summary

We are building a set of management APIs to enable common announcement operations (post, schedule) across announcement platform dispatchers.

#### What is Announcer API?

- An API definition for managing Announcement declaratively.

## Glossary

- __Announcer API__: Unless otherwise specified, this refers to the project as a whole.
- __Announcement dispatcher__: Refers to the platform where announcement is going to be dispatched. Examples include Telegram, Twitter, Meetup.com, etc.
- __Dispatcher implementation__: Existing Announcer API implementations consist of generic and platform dispatcher-specific logic. The platform dispatcher-specific logic is currently maintained in the same repo.

## Motivation

We want to control and automate dispatching announcements for multiple purposes to various annoncement platforms, which includes announcing meetup information, scheduling kubeweekly content, promoting workshop events, and many more. We want to use Kubernetes programming techniques to implement the project which is meant to be a showcase of Kubernetes extension mechanism.

### Goals

- To manage the operation (post, schedule) of announcements using a declarative API.
- To work in different announcement platforms.
- To define common operations, provide a default implementation, and provide the ability to swap out implementations for alternative ones.

### Non-goals

- To manage non-Announcer API dispatched announcements.
- To scrape kubeweekly contents.
- To configure and create bots or accounts for dispatching announcements.

## Requirements

#### Foundation

- Announcer API MUST be able to be deployed and run on Kubernetes.

- Announcer API MUST support multiple announcement platforms.

- Announcer API MUST be able to dispatch announcements in real-time as well as scheduled in specific time.

#### User Experience

- Announcer API MUST be able to provide the configuration of announcement platform where announcements are dispatching to.

#### Extension

- Announcer API SHOULD allow default implementations to be pluggable/extensible.
   - Announcer API SHOULD offer default implementations for generic operations.

- Announcer API MUST be able to provide a consistent (across dispatchers) way to prepare, post, and schedule announcements.

- Announcer API MUST provide the ability to receive the  status of a dispatched announcement.
