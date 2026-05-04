# CartScale

Production-style shopping cart and checkout system focused on concurrency, idempotency, and safe state transitions.

## Overview

CartScale is a production-style backend system exploring how modern shopping cart and checkout systems are designed for reliability under load.

The project focuses on the difficult parts of commerce systems:

- concurrent cart updates
- stock reservation
- idempotent checkout
- retry safety
- async order processing
- safe state transitions

The goal is to model a commerce system the way real production systems are built, not just how tutorials implement carts.

## Why This Exists

Most shopping cart examples stop at CRUD.

Real commerce systems are harder.

The complexity is not in adding items to a cart.
The complexity is in handling concurrency, consistency, retries, stock safety, and operational reliability.

CartScale exists to explore how production-grade cart systems behave under real conditions.

This project focuses on the parts that usually fail first:

- duplicate checkout requests
- stock overselling
- race conditions
- stale cart state
- retry collisions
- payment consistency
- asynchronous fulfilment flows

## Core Concepts

CartScale is built around a few core engineering concerns:

### Cart State Management
Carts behave as mutable user state with controlled updates, expiry handling, and predictable state transitions.

### Stock Reservation
Inventory is reserved during checkout flow to reduce oversell risk and support safe fulfilment.

### Idempotent Checkout
Checkout must be safe to retry without duplicate orders or double processing.

### Order State Transitions
Orders move through explicit state transitions with validation and controlled side effects.

### Async Processing
Non-blocking background workflows handle fulfilment, notifications, and post-checkout processing.

### Operational Safety
The system is designed to fail safely under retries, duplicate requests, and partial failure scenarios.

## Architecture (MVP)

Cart → Cart Items → Reservation → Checkout → Order → Fulfilment Events

The MVP is focused on correctness, consistency, and safe state handling under load.

## Tech Stack

- Django
- PostgreSQL
- Redis
- Celery
- Django REST Framework
- Docker

## Roadmap

- Cart service
- Cart item lifecycle
- Stock reservation
- Checkout flow
- Idempotency handling
- Order state machine
- Async fulfilment
- Retry safety
- Containerised local development

## Current Status

Currently in active development.

This repository is focused on establishing the core cart lifecycle, reservation flow, and checkout safety model first, followed by order orchestration and async fulfilment.

## Project Goal

Build a production-style commerce backend that reflects how real shopping cart and checkout systems are designed for correctness, resilience, and scale.
