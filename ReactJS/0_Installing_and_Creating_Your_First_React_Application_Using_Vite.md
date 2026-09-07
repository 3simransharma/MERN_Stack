# Practical 1: Creating Your First React Application Using Vite

## Objective

In this practical, you will learn how to:

- Install Node.js
- Verify the installation
- Create your first React application using Vite
- Run the React application
- Open and run the project again later

## Prerequisites

Before starting this practical, make sure you have:

- Node.js (LTS Version)
- Visual Studio Code (VS Code)
- An internet connection (required only during installation)

# Step 1: Install Node.js

## Why do we need Node.js?

React projects use **Node.js** to install packages and run the development server. Without Node.js, we cannot create or run a React application.

## Installation

1. Visit the official website: **https://nodejs.org/**
2. Download the **LTS (Long Term Support)** version.
3. Run the installer and follow the installation steps until it finishes.

# Step 2: Verify the Installation

After installing Node.js, let's make sure it has been installed correctly.

Open **Command Prompt** or **Terminal** and run:

```bash
node -v
```

### Expected Output

```text
v24.5.0
```

If you see a version number, Node.js has been installed successfully.

Now check the npm version:

```bash
npm -v
```

> **Note:** npm (Node Package Manager) is installed automatically along with Node.js.

# Step 3: Open Visual Studio Code

1. Open **Visual Studio Code**.
2. Open or create a folder where you want to save your React project.
3. Open the terminal.

You can open the terminal using:

**Menu:** `Terminal → New Terminal`

or

**Shortcut:** `Ctrl + \``

# Step 4: Create a React Application

Run the following command in the terminal:

```bash
npm create vite@latest my-react-app -- --template react
```

## Understanding the Command

| Part | Description |
|------|-------------|
| `npm` | Node Package Manager |
| `create vite@latest` | Creates a new Vite project |
| `my-react-app` | Name of the React project (you can change it) |
| `--template react` | Creates a React application |

## Installation Process

During installation, you may see:

```text
Need to install the following packages:
create-vite@9.1.1

Ok to proceed? (y)
```

Type:

```text
y
```

and press **Enter**.

Next, select:

- **Which linter to use?** → **Oxlint**
- **Install with npm and start now?** → **Yes**

## What Happens Next?

Vite will:

- Create a new React project.
- Install all the required packages.
- Start the development server automatically.

You will see an output similar to:

```text
VITE v8.1.5 ready

➜ Local: http://localhost:5173/
```

Open the **Local** URL in your web browser.

If everything is correct, you will see the default React page.

Congratulations! You have successfully created your first React application.

# Step 5: Stop the Development Server

To stop the development server, simply press:

```text
Ctrl + C
```

# Opening the Project Again

Whenever you want to continue working on your project, follow these steps.

## Step 1: Open the Project

Open the **my-react-app** folder in Visual Studio Code.

## Step 2: Open the Terminal

Open a new terminal.

## Step 3: Move to the Project Folder

```bash
cd my-react-app
```

## Step 4: Install Dependencies (Only if Needed)

If the **node_modules** folder is missing, run:

```bash
npm install
```

> Normally, you do not need to run this command every time. Run it only if the `node_modules` folder is missing.

## Step 5: Start the React Application

Run:

```bash
npm run dev
```

You will again see a Local URL similar to:

```text
➜ Local: http://localhost:5173/
```

Open this URL in your browser to start the application.

# Commands Used

| Command | Purpose |
|---------|---------|
| `node -v` | Check whether Node.js is installed |
| `npm -v` | Check the npm version |
| `npm create vite@latest my-react-app -- --template react` | Create a new React application |
| `cd my-react-app` | Move into the project folder |
| `npm install` | Install project dependencies (only if needed) |
| `npm run dev` | Start the React development server |
| `Ctrl + C` | Stop the development server |

# Conclusion

In this practical, you learned how to install Node.js, verify the installation, create a React application using Vite, run the application, stop the development server, and open the project again whenever required.
