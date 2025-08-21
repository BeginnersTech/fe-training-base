# Next.js + Tailwind CSS ToDo App Training

This document is a training guide for building a simple ToDo application using Next.js and Tailwind CSS. Through this training, you will practice the fundamentals of modern web application development and ultimately build a working ToDo application.

## Objectives

The main objectives of this training are:

- Understand the basic project structure and routing in Next.js.
- Learn efficient styling with Tailwind CSS.
- Design and implement reusable UI components.
- Consider UI/UX principles when designing the application.

## How to Proceed

This training progresses through the major steps below. Each step includes detailed tasks and features to implement. Follow the instructions and proceed step by step. After completing each step, create a pull request and request a review.

## Design Resources

We provide the design for this training in Figma. Please create the deliverables for each step according to the Figma design.

- [Figma](https://www.figma.com/design/gGF072fcZ2pqvwWkeHK0uU/%E7%A0%94%E4%BF%AE%E7%94%A8PJ?node-id=0-1&t=ybqJnqP8ml7bJPNv-1)

## Prerequisites

Please fork this repository into your own project by following the instructions in [this guide](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo).

---

## Step 1: Define Design Tokens

In this step, you will define design tokens in Tailwind CSS so that a consistent design can be applied throughout the application. Design tokens are a way to manage design attributes such as colors, spacing, and border radii using numbers and names. This makes design changes easier and improves development efficiency.

### Tasks

Add the following semantic design tokens inside the `@theme inline {}` block in `src/app/globals.css`.
For more details, see the [official Tailwind theme docs](https://tailwindcss.com/docs/theme).

- **Border radius (`--radius-*`)**:

  - `--radius-1: 5px;`
  - `--radius-2: 10px;`

- **Colors (`--color-*`)**:

  - `--color-primary: #818cf8;`
  - `--color-background: #ffffff;`
  - `--color-foreground: #1f2937;`

- **Spacing (`--spacing-*`)**:
  - `--spacing-sm: 8px;`
  - `--spacing-md: 16px;`
  - `--spacing-lg: 24px;`

By defining these tokens, you can apply a unified design across the application via Tailwind utility classes. For example, once you define the `primary` color, you can consistently apply the brand color by simply using classes like `bg-primary` on buttons and links.

---

## Step 2: Create Components

In this step, you will create the basic components that make up the application's UI. Components are reusable building blocks that improve maintainability and extensibility. Create each component inside the `src/components` directory and design them with single responsibility in mind.
Also, use the design tokens from Step 1 for styling.

### Tasks

Create the following UI components under `src/components`:

- `TextField.tsx`: A text input field for users. Used for adding and editing tasks.
- `Button.tsx`: A clickable button. Used for registering, editing, deleting tasks, and navigating between screens.
- `List.tsx`: A container for displaying multiple items. Used for the ToDo list.
  - `ListItem.tsx`: A component representing an individual list item used within `List`. Displays each ToDo task.
- `Header.tsx`: The header component of the application. Only the application logo is placed here. Please use the `logo.svg` file located in the `public` folder for the logo.

These components will be combined in later steps to build the screens. It is important that each component can be flexibly configured via props.

---

## Step 3: Create Layout

In this step, you will define the global application layout. In Next.js, the `src/app/layout.tsx` file serves as the root layout, where you can place common UI elements for all pages.

### Tasks

Open `src/app/layout.tsx` and define the overall layout of the application.

- **Global Layout**: Place the `Header` component at the top of the screen and display the main content below it. This ensures the header is always visible regardless of page navigation.

This layout is critical for maintaining visual consistency across the application. The main content area should accept `children` to dynamically render page content.

---

## Step 4: Build Screens

In this step, you will create the two main screens of the ToDo application: the Home screen and the Edit screen. Each screen will be built by combining the components created so far. Read the specifications carefully and implement them accurately.

### Tasks

#### Home Screen

Create `index.tsx` under the `src/features/home` directory and implement the Home screen. This screen is the entry point for adding tasks, listing tasks, and editing/deleting tasks.

- **Header**: Place the common `Header` component at the top of the screen. (Since the header is already placed in `layout.tsx`, you do not need to place it again in the Home screen.)
- **Task Input Field**: Place the `TextField` component for entering a new task name.
- **Register Button**: Place the `Button` component. This button should behave as follows:
  - When clicked, the entered task is registered in the application. (For this training, you will not actually use an API or persist to a DB; it is sufficient to store the data in some state variable and display it in the list.)
  - When registration succeeds, show a notification to the user using the standard JavaScript `alert()` function: "Registration successful".
  - **Important**: When the `TextField` is empty, this button must be disabled (not clickable) to prevent registering empty tasks.
- **Task List**: Use the `List` component to display the registered ToDo tasks. Each task should be displayed as a `ListItem` with the following elements:
  - **Task Name**: Displays the name of the registered task.
  - **Edit Button**: Place a `Button` that navigates to the Edit screen for the selected task.
  - **Delete Button**: Place a `Button` that deletes the selected task from the application. Upon successful deletion, show a notification using the standard JavaScript `alert()` function: "Deletion successful".

#### Edit Screen

Create `index.tsx` under the `src/features/edit` directory and implement the Edit screen. This screen is used to modify existing ToDo tasks.

- **Header**: Place the common `Header` component at the top of the screen. (Since the header is already placed in `layout.tsx`, you do not need to place it again in the Home screen.)
- **Task Name Input Field**: Place the `TextField` component with the following behavior:
  - When navigated from the Home screen's edit button, the current name of the selected task should be pre-filled in this field and can be modified by the user.
- **Register Button**: Place the `Button` component. This button should behave as follows. (For this training, you will not actually use an API or persist to a DB; it is sufficient to store the updated data in some state variable and reflect it in the list.)
  - When clicked, the task name changed in the `TextField` is registered (updated) in the application.
  - When the update succeeds, show a notification using the standard JavaScript `alert()` function: "Edit saved successfully".
- **Cancel Button**: Place a `Button` that closes the current Edit screen and returns to the Home screen (the screen from which the Edit screen was opened).

---

## Final Deliverable

The final deliverable of this training is a working ToDo application that has completed all the steps above. This `README.md` file itself is also an important deliverable summarizing the training content.

---
