React TRUE Vim Component
========================
[![Build Status](https://travis-ci.org/rhysd/react-vimjs.svg)](https://travis-ci.org/rhysd/react-vimjs)

This is a [Vim.js](https://github.com/coolwanglu/vim.js) component for [React.js](https://facebook.github.io/react/).  You can easily introduce Vim into your React.js web application.

Please try [Markdown Demo](http://rhysd.github.io/react-vimjs/).  The source code of this demo is [here](example).

## Install

Not yet.

## Usage

### Basic Usage

You can use `<Vim>` component.

- `index.js`

```javascript
import Vim from 'react-vimjs'

React.render(
  <Vim memPath="path/to/vim.js.mem"> Loading... </Vim>,
  document.body
);
```

- `index.html`

```html
<html>
  <head>
    <meta charset="utf-8" />
    <title>Hello, react-vimjs</title>
    <link rel="stylesheet" href="node_modules/react-vimjs/dist/vim.css">
  </head>
  <body>
  </body>
  <script src="path/to/index.js"></script>
  <script src="path/to/vim.js"></script>
</html>
```

You need to link `vim.css` in `dist` directory and load `vim.js` with `<script>` tag after loading your `index.js`.  And set path to `vim.js.mem` as property of `<Vim>` component.
`<Vim>` has many other optional properties. (Document is TODO)

Basically all files are put on memory so it is volatile after closing the page.  Only `.vimrc` is saved to local storage.

### Edit Local File

You can load local file with file chooser easily with `<FileUpload>` component.

```javascript
import Vim,{FileUpload} from 'react-vimjs'

React.render(
  <div>
    <Vim memPath="path/to/vim.js.mem"> Loading... </Vim>
    <FileUpload onUpload={(dir, name) => alert("Loaded " + dir + "/" + name)}>
      <button type="button">
        Edit Local File
      </button>
    </FileUpload>
  </div>,
  document.body
);
```

Children of `<FileUpload>` component gets clickable.  When clicked, `<input>` file chooser is launched and you can select a file.  If `onUpload` property is set, it is called with the path to loaded file after loading the file is success.  When `blah.txt` is selected, `/root/blah.txt` is created in Emscripten filesystem and you can open it with `:edit blah.txt`.


