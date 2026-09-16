# MessManagement

MessManagement is a meal and shared-expense management system for people living together in messes, hostels, and bachelor accommodations.

It helps mess members record daily meals, manage contributions, calculate monthly meal costs, and understand who needs to pay or receive money.

## Project Idea

Managing meals and shared expenses manually can be confusing when different members eat different numbers of meals, contribute different amounts of money, or bring guests.

MessManagement aims to make this process simple, transparent, and organized through one application.

## Basic Features

* Create and manage a mess group.
* Add and manage mess members.
* Record daily breakfast, lunch, and dinner.
* Cancel meals when a member will not eat.
* Add guest meals.
* Record member contributions.
* Calculate the monthly meal rate.
* Calculate each member’s meal cost and balance.
* View monthly reports and previous records.
* Support different user roles and permissions.

## Basic Calculation

```text
Meal rate = Total contributions / Total meals

Member meal cost = Member meals × Meal rate

Member balance = Member contribution − Member meal cost
```

A positive balance means the member should receive money.

A negative balance means the member needs to pay money.

## How We Are Building It

MessManagement is being developed as a real software engineering project.

Our planned development direction includes:

* **C** for learning and developing the core calculation logic.
* **C# and ASP.NET Core** for the backend.
* **PostgreSQL** for data storage.
* **Flutter and Dart** for the mobile application.
* **Git and GitHub** for version control and team collaboration.

The technology stack may evolve as we learn and make better technical decisions.

## Development Philosophy

We are building this project to understand software engineering—not just to make an application quickly.

Our principles are:

* Understand the problem before writing code.
* Learn the fundamentals behind every technology.
* Avoid blindly copying and pasting code.
* Do not use code that we cannot explain.
* Write code ourselves and understand how it works.
* Use documentation and learning resources responsibly.
* Ask for help when necessary, but understand the solution afterward.
* Break large problems into smaller problems.
* Test our code and learn from mistakes.
* Prefer clear, maintainable code over unnecessarily complicated code.
* Review each other’s work and share knowledge.
* Improve the project gradually through small, meaningful changes.

**The goal is not only to finish MessManagement. The goal is to become better software engineers while building it.**

## Team Workflow

We use Git and GitHub to collaborate.

Our general workflow is:

1. Understand and discuss a task.
2. Create a separate feature branch.
3. Implement the task.
4. Test the changes.
5. Commit the work with a clear message.
6. Push the branch to GitHub.
7. Review the changes.
8. Merge the work into `main`.

The `main` branch should contain stable and reviewed code.

## Project Status

MessManagement is currently in the planning and foundation stage.

We are focusing on:

* Finalizing requirements.
* Designing the calculation rules.
* Planning the project architecture.
* Setting up the development environment.
* Establishing professional Git and GitHub practices.
* Building the project step by step.