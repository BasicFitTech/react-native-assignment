# React Native Assignment the workout player


Build a small standalone **workout player** app that allows users to start and complete a workout.

The main focus of this assignment is not the number of features you implement, but **how you approach the problem**. We want to see how you structure the application, manage state, handle persistence, and make technical decisions.

## Time limit

The assignment is designed to take approximately **4 hours**.

Please stop working when you reach the 4-hour mark, even if the assignment is not completely finished. If anything remains, document what is still missing and briefly explain how you would approach it.

We are more interested in your **engineering decisions and approach** than in completing every possible detail.

---

# Requirements

### 1. Workout player

Build a workout player based on the provided design.

A user should be able to:

1. Open a workout.
2. Start the workout.
3. Progress through the exercises.
4. See the current exercise and relevant workout information.
5. Complete the workout.

The workout should follow the structure provided by the Contentful data.

### 2. Rest timer

During a rest period, display a countdown timer.

Users should be able to:

* Add **15 seconds**
* Remove **15 seconds**
* See an animation
* Move to the next exercise when the rest period is complete

The timer should not be able to go below zero.

### 3. Persist workout progress

The current workout progress must survive the app being closed and reopened.

For example:

> A user is halfway through a workout, closes the app, and opens it again later.

The workout should resume from the appropriate state instead of starting from the beginning.

Consider what information needs to be persisted to correctly restore the workout.

When the workout is completed, the active workout state should be cleared.

---

# Data

Workout data is available through our Contentful GraphQL API:

[Contentful GraphQL API](https://graphql.contentful.com/content/v1/spaces/ztnn01luatek/environments/TEST/explore?access_token=wRd4zwNule_XU0IrbE-DSfF0IcFxSnDCilyboUhYLps)

You can use the following query as a starting point:

```graphql
query {
  workoutCollection(
    where: { sys: { id_in: ["1qxS37UJepjiXhLPVqM8tX"] } }
  ) {
    items {
      sys {
        id
      }
      warmUp
      powerSet
      picture {
        url
      }
      coolDown
    }
  }

  exerciseCollection(
    where: { sys: { id_in: ["5DM31eT4upmPt3vdonUEth"] } }
  ) {
    items {
      name
      vixyVideo
      sys {
        id
      }
    }
  }
}

```

You are free to structure the GraphQL queries differently or use a different workout if you prefer.

---

# Videos

You **do not need to implement video playback**.

An exercise thumbnail is sufficient.

You can construct the thumbnail URL using the `videoId`:

```text
https://static.cdn.vixyvideo.com/p/380/thumbnail/entry_id/${videoId}
```

---

# Technical requirements

The application must be built using:

* **React Native**
* **TypeScript**


You are free to choose the appropriate solution for:

* Local workout state
* Persistence
* Component structure
* Navigation
* Animations
* State management

We are interested in the reasoning behind these choices.

---

# Design

The design is shown below:

![Workout Player design](example-design.png)

The implementation does not need to reproduce every pixel exactly, but the overall UI and interaction should follow the provided design.

---

# Technical decisions

There is no single correct architecture for this assignment.

Please make pragmatic technical choices appropriate for the scope of the application.

In your README, briefly explain:

* How you structured the application
* How you manage server state
* How you manage local workout state
* How you persist and restore workout progress
* Any significant trade-offs or assumptions you made

Keep this short a few paragraphs or bullet points are enough.

---

# Edge cases

You do not need to implement every possible edge case, but consider how your solution handles situations such as:

* The app is closed while a workout is in progress
* The app is closed during a rest timer
* The user completes the workout
* The API request fails
* Workout data is unavailable
* The rest timer reaches zero
* The user repeatedly adds or removes time

If you don't have time to implement a particular edge case, document how you would handle it.

---
# Ai

You may use it, but we ask you to mention it in the README: what you used and why, and anything it got wrong and why it went wrong.

Not mentioning it at all is the only thing that would count against you.

---

# Code quality

We are looking for code that is:

* Readable
* Maintainable
* Well typed
* Appropriately structured
* Easy to extend

Avoid over-engineering the solution. A simple, well-reasoned implementation is preferable to a complex architecture that isn't justified by the scope.

---

# What we will evaluate

We will primarily look at:

### React Native

* Understanding of React Native fundamentals
* Component design
* Hooks and lifecycle
* Appropriate handling of asynchronous behavior
* Performance awareness where relevant

### Architecture

* Separation of concerns
* State management decisions
* Server state vs. local state
* Persistence strategy
* Ability to keep the solution maintainable

### TypeScript

* Appropriate types
* Type safety
* Avoidance of unnecessary `any` or unsafe type assertions

### Engineering judgment

* How you prioritize within the 4-hour constraint
* Handling of edge cases
* Simplicity vs. over-engineering
* Technical trade-offs
* Ability to explain your decisions

### User experience

* Following the provided design
* Clear workout progression
* Correct timer behavior
* Correct restoration of workout state

---


# Submission

Please provide:

* The source code
* A README with setup instructions
* A short explanation of your main technical decisions
* Any known limitations or unfinished work

If you reach the 4-hour limit, stop and clearly document what remains.

**Good luck!**
