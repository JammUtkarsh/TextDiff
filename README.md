# Text Diff

`git diff`, but for text.

## Working

The user enters two versions of text through the client-side application. The client-side application then makes a `POST` request to the backend.
The backend is composed of two components.

- **API gateway**: This is the entry point for the client-side application. It will receive the data from the client. It will perform the basic checks, like field validation. Finally, it will forward the data to the diff engine.
- **Diff Engine**: This is the core component of the application. It will receive the data from the API gateway. It will then perform an operation similar to `git diff` on the data. Finally, it will return the result.

The communication between the client and API gateway will be done using REST. The communication between the API gateway and the diff engine will be done using gRPC.

## Features

Here are some of the features that will be implemented after the MVP:

- [ ] Ability to upload files.
- [ ] Message queue application like Kafka between API gateway and diff engine.
- [ ] Make the diff engine scalable.
- [ ] Ability to save the difference.
- [ ] Multi-version diff.

## Architecture

### Web UI

- The web UI will be the client-side application.
- The user will simply be able to upload the left and right files or data.
- The web UI will be a single-page application.

### REST API server

- The REST API server will be the entry point for the client-side application.
- It will act as the API gateway for the client.
- Once both the left and right files are uploaded, the REST API server will send the data to the diff engine.
- The data will be sent using gRPC.

#### Endpoints

- [ ] `POST /` - Upload the two versions of text.
- [ ] `GET /` - Get diff result

### Diff Engine

#### Overview

- Using gRPC, the data will be fed to the diff engine.
- Upon processing the data, the diff engine will return the result to the REST API server.
- The REST server will then return the result to the client.

### Highlights

- The **Diff Engine** will be written in **Go**.
  - This will allow us to use the concurrency features of Go.
  - Personally, I want to learn how to build scalable applications, and I want to use Go as a tool for that.
- The **API gateway** will be written in **Python**.
  - Personally, I want to learn how to build a REST API using Python.
  - We will be using FastAPI for the REST API server.
  - Optionally, we will also build a version with Flask for the REST API server.
- The **Web UI** will be written in **TypeScript**.
  - We will be using [shadcn/ui](https://ui.shadcn.com/docs) for the web UI and building on top of it.
