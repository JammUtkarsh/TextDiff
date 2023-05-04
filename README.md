# Text Diff

`git diff`, but for text.

## Problem Statement

One of the tools that I use often while writing blogs and other documents is [QuillBot](https://quillbot.com/) and [Grammerly](https://www.grammarly.com/). These tools, eridicate grammatical errors and spelling mistakes with a single click(especially in QuillBot).

However, instead of giving a **new** corrected version, it updates the **existing** text on the screen. This is a problem I want to solve. I want to keep track of the changes that the app has made.

## Solution

The solution is to build a tool that will show the difference between the two versions of text. This will allow me to keep track of the changes that the app has made.

Hence, `Text Diff` was born.

## Working

The user enters two versions of text through the client-side application. The client-side application then makes a `POST` request to the backend.
The backend is composed of two components.

- **API gateway**: This is the entry point for the client-side application. It will receive the data from the client. It will perform the basic checks, like field validation. Finally, it will forward the data and metadata to the diff engine.
- **Diff Engine**: It is the core component of the application. After recieving the data, it will then perform an operation similar to `git diff`and return the result.

## Architecture

### Web UI

- The web UI will be the client-side application.
- The user will upload the *current* and *updated* version of data

### REST API server

- It will act as the API gateway for the client.
- Once both the *current* and *updated* version are recieved, the REST API server will send the data to the diff engine using gRPC.
- The communication between the client and API gateway will be done using RESTful APIs.

#### Endpoints

- [ ] `POST /` - Upload the two versions of text.

### Diff Engine

#### Overview

- Upon recieving the data from the API gateway, the diff engine will perform the diff operation.
- After processing, the diff engine will return the result to the API gateway.
- The communication between the API gateway and the diff engine will be done using gRPC.

### Highlights

- The **Diff Engine** will be written in **Go**.
  - This will allow us to use the concurrency features of Go.
  - Personally, I want to learn how to build scalable applications, and I want to use Go as a tool for that.
- The **API gateway** will be written in **Python**.
  - Personally, I want to learn how to build a REST API using Python.
  - We will be using FastAPI for the REST API server.
  - Optionally, we will also build a version with Flask for the REST API server.
- The **Web UI** will be written in **TypeScript**.
  - Would need frontend dev for this to make design decisions.
  - It needs to lightweight and fast.
  - The functional components include: 2 text-area, 1 button and 1 result area.
  - We plan to [shadcn/ui](https://ui.shadcn.com/docs)

## Features(Future)

Here are some of the features that will be implemented after the MVP:

- [ ] Ability to upload files.
- [ ] Message queue application like Kafka between API gateway and diff engine.
- [ ] Make the diff engine scalable.
- [ ] Ability to save the difference.
- [ ] Multi-version diff.

## Something about me related to this project

I am building this project to learn a lot of things and to build something that I can use in my daily life.

Here are some of things that I want to learn and try out:

- [ ] How to build a REST API using Python.
- [ ] How to build a gRPC server using Go.
- [ ] Understand the concurrency in Go.
- [ ] Understanding and Using Message Queues. Learn Kafka.
- [ ] How to integrate a backend with frontend.
- [ ] Learn System Design
- [ ] Follow the Software Engineering practices. Especially designing before coding.
