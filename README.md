# Simple Notepad

A lightweight notes app built with Node.js, Express and EJS. There is no database: every note is saved as a plain `.txt` file on the server using Node's built-in `fs` module.

## Features

- Create a note with a title and details
- Browse all your notes as cards on the home page
- Open any note to read its full content
- Rename a note's file from its card with the "edit filename" link
- Clean dark UI styled with Tailwind CSS

## Tech Stack

- **Node.js** and **Express**: server and routing
- **EJS**: server-side templates
- **Tailwind CSS** (via CDN): styling
- **fs module**: reading, writing and renaming notes as files

## How It Works

| Route             | Method | What it does                                                         |
| ----------------- | ------ | -------------------------------------------------------------------- |
| `/`               | GET    | Reads the `files` folder with `fs.readdir` and lists every note      |
| `/create`         | POST   | Saves a new note as `files/<TitleWithoutSpaces>.txt`                 |
| `/file/:filename` | GET    | Reads that note with `fs.readFile` and shows it on its own page      |
| `/edit/:filename` | GET    | Shows a form with the current file name and a box for the new name   |
| `/edit`           | POST   | Renames the file with `fs.rename`, then redirects back to the home page |

> **Note:** The rename uses the new name exactly as typed and does not add `.txt` for you, so type the full name (for example `goals.txt`).

## Getting Started

```bash
git clone https://github.com/VrxGhost/simplenotepad.git
cd simplenotepad
npm install
node index.js
```

Then open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
├── files/            # notes are saved here (ignored by git)
├── public/
│   └── stylesheets/
├── views/
│   ├── index.ejs     # home page: form + list of notes
│   ├── show.ejs      # single note page
│   └── edit.ejs      # rename form for a note's file
├── index.js          # Express server and routes
└── package.json
```

## What I Learned

- Setting up an Express server with EJS as the view engine
- Serving static files from a `public` folder
- Reading form data with `express.urlencoded` and `req.body`
- Using route params (`req.params`) to build dynamic pages
- Working with the file system using `fs.readdir`, `fs.readFile`, `fs.writeFile` and `fs.rename`
- Passing data from the backend to EJS and looping over it with `forEach`
- Links (`<a href>`) always send GET requests, so a page opened from a link needs an `app.get` route
- Giving form inputs different `name`s so the server can tell them apart in `req.body`

## Future Improvements

- Edit a note's content, and delete notes
- Add `.txt` automatically when renaming a file
- Validate file names to keep reads inside the `files` folder
- Store notes in a database instead of the file system
