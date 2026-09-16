# Paws and Found 

This is the official repository for Paws and Found. This outlines the technical specifications required to configure your local development environment and ensure a seamless workflow across the team.

## 1. Project Setup and Prerequisites

Every team member must configure their local environment precisely to support the cross-platform mobile framework and backend services.

1. Download and install the latest Flutter SDK and Android Studio. For groupmates using Windows Home editions, you must strictly check the "Android Emulator hypervisor driver" in the Android Studio SDK Manager to ensure virtual devices run correctly.
2. Download and install Docker Desktop. This is mandatory for hosting our local Supabase instance and containerizing the external OpenCV engine.
3. Open your terminal and clone this repository using the command `git clone https://github.com/NaesCode/Paws_and_Found`.
4. Navigate into the cloned project folder and execute the command `flutter pub get` to download all necessary Dart packages.
5. Run `flutter doctor` to confirm there are no missing components in your SDK path.

## 2. Backend and OpenCV Initialization

Our architecture relies on Supabase for the PostgreSQL database and a Python container for the artificial intelligence image matching.

1. Launch Docker Desktop and ensure the Docker engine is actively running in the background.
2. Open your terminal in the project root and execute `supabase start` to spin up the PostgreSQL database, Storage buckets, and Edge Functions locally.
3. Change directories into the backend AI folder and run `docker-compose up -d` to boot the OpenCV image processing container in detached mode.
4. Confirm that the PostGIS spatial extensions and database schemas are properly loaded before attempting to render the localized community map.

## 3. Branching Naming Conventions

To prevent merge conflicts before our strict November code freeze, absolutely no one is allowed to push directly to the main branch. Always create a new branch for your specific task using the prefixes outlined below.

| Branch Prefix | Usage | Example |
| :--- | :--- | :--- |
| `feature/` | Developing new core components | `feature/opencv-matching` |
| `bugfix/` | Resolving issues from the GitHub tracker | `bugfix/map-crash` |
| `ui/` | Frontend updates and Flutter layout tweaks | `ui/feed-screen` |
| `docs/` | Updating the SDD, SPMP, or README | `docs/update-setup` |

## 4. Commit Message Standards

Clear commit messages are vital for tracking our progress against the project schedule. Every commit must follow standard conventions and reference the active GitHub Issue number.

| Type | Example |
| :--- | :--- |
| **feat:** | feat: integrate OpenCV similarity scoring (#12) |
| **fix:** | fix: resolve PostGIS spatial query timeout (#15) |
| **chore:** | chore: update Flutter dependencies |
| **refactor:** | refactor: optimize Supabase storage triggers |
