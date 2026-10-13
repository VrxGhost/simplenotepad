# Notes App

A simple notes app built with Node.js, Express and EJS. There is no database: each note is saved as a `.txt` file using Node's built-in `fs` module.

Built while following the [Sheryians Coding School](https://www.youtube.com/@sheryians) backend development series.

## Features

- Create a note with a title and details
- See all your notes as cards on the home page
- Open a note to read its full content
- Dark UI styled with Tailwind CSS

## Tech Stack

- **Node.js** and **Express**: server and routing
- **EJS**: server-side templates
- **Tailwind CSS** (via CDN): styling
- **fs module**: reading and writing notes as files

## How It Works

| Route              | Method | What it does                                                     |
| ------------------ | ------ | ---------------------------------------------------------------- |
| `/`                | GET    | Reads the `files` folder with `fs.readdir` and lists every note  |
| `/create`          | POST   | Saves a new note as `files/<TitleWithoutSpaces>.txt`             |
| `/file/:filename`  | GET    | Reads that note with `fs.readFile` and shows it on its own page  |

## Getting Started

```bash
git clone <your-repo-url>
cd <repo-folder>
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
│   └── show.ejs      # single note page
├── index.js          # Express server and routes
└── package.json
```

## What I Learned

- Setting up an Express server with EJS as the view engine
- Serving static files from a `public` folder
- Reading form data with `express.urlencoded` and `req.body`
- Using route params (`req.params`) to build dynamic pages
- Working with the file system using `fs.readdir`, `fs.readFile` and `fs.writeFile`
- Passing data from the backend to EJS and looping over it with `forEach`
