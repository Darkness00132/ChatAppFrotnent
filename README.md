# Frontend Chat Feature – Engineering Overview

## Overview

This project implements a **real‑time chat feature** using modern frontend tools. The focus is on **clean architecture, correct state handling, and reliable integration with authentication and real‑time services**, rather than UI complexity.

The code is structured to be **easy to understand, safe to extend, and suitable for real applications**.

***

## Key Highlights

*   Real‑time messaging using **SignalR**
*   Clear separation between **UI, logic, networking, and state**
*   Centralized and defensive **authentication handling**
*   Predictable async state with **React Query**
*   Runtime‑safe validation using **Zod**

***

## Architectural Decisions

### Real‑Time Logic Isolation

All SignalR behavior is encapsulated in a dedicated hook (`useChat`).  
UI components interact with chat functionality through a simple interface, without knowing implementation details.

**Benefit**: cleaner components, reusable logic, easier maintenance.

***

### Rooms vs Messages

*   Chat rooms are mocked on the frontend
*   Messages always come from the real‑time connection

**Benefit**: realistic real‑time behavior while keeping UI development flexible.

***

### Centralized Authentication

Authentication is handled once and reused everywhere:

*   Access token stored globally
*   Axios interceptors manage token attachment and refresh
*   SignalR uses the same token source

**Benefit**: avoids duplicated logic and common auth edge cases.

***

### Predictable Side Effects

*   Network logic lives in service layers
*   Business logic lives in hooks
*   Components focus only on rendering and interaction

**Benefit**: easier reasoning and safer future changes.

***

## Validation & Data Flow

*   User input validated at runtime using **Zod**
*   Types inferred directly from schemas
*   Async mutations handled with **React Query**

**Benefit**: strong contracts and fewer runtime errors.

***

## Design Note

The UI is intentionally simple. Visual polish is not the goal of this project; the emphasis is on **engineering quality, correctness, and structure**.

***

