# 🦖

```
__        ___    ____  __  __   _____      _             _       _
\ \      / / \  / ___||  \/  | |_   _|   _| |_ ___  _ __(_) __ _| |
 \ \ /\ / / _ \ \___ \| |\/| |   | || | | | __/ _ \| '__| |/ _` | |
  \ V  V / ___ \ ___) | |  | |   | || |_| | || (_) | |  | | (_| | |
   \_/\_/_/   \_\____/|_|  |_|   |_| \__,_|\__\___/|_|  |_|\__,_|_|

```

      ▶ Quick Intro

      ▶ How to use SetUp a WebPage for WASM

      ▶ Writing a WASM Module

      ▶ Integrate WASM in a WebPage

      ▶ Testing

      ▶ Outro & chitchat

# 🦖🦖

```
 / _ \ _   _(_) ___| | __ |_ _|_ __ | |_ _ __ ___
| | | | | | | |/ __| |/ /  | || '_ \| __| '__/ _ \
| |_| | |_| | | (__|   <   | || | | | |_| | | (_) |
 \__\_\\__,_|_|\___|_|\_\ |___|_| |_|\__|_|  \___/

```

# 🦖🦖🦖

```
 ____       _   _   _
/ ___|  ___| |_| | | |_ __
\___ \ / _ \ __| | | | '_ \
 ___) |  __/ |_| |_| | |_) |
|____/ \___|\__|\___/| .__/
                     |_|
```

Initialize a new Rust Project

```sh
cargo init
```

Initialize a new WebApp Project via NodePackageManger

```sh
npm init -y
```

Install all necessary dependencies.

```sh
npm install -D webpack webpack-cli webpack-dev-server html-webpack-plugin
```

Create a file for configuring the Webpack.

```sh
touch webpack.config.js
```

Set up webpack.config.js

```js
module.exports = {};
```

Create a bare minimum HTML set

```sh
mkdir public
touch public/index.html
touch public/main.js
```

Write in index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title></title>
  </head>
  <body>
    <h2>🚀Hello WASM🚀</h2>
    <p>This is a WASM Application</p>
    <label for="">
      <input type="file" id="inpute" accept=".png" class="hidde" />
      Upload an image 🦖
    </label>
    <img id="new-image" />
    <script>
      import * from main.js
      console.log("Hello World")
    </script>
  </body>
</html>
```

Content of webpack.config.js

```js
const path = require('path')
const HTMLWebpackPlugin = require('html-webpack-plugin')

module.exports = {
    entry: './public/main.js',
    output: {
        path=path.resolve(__dirname, 'dist'),
        filename= 'index.js'
      },
      plugins: [
      new HTMLWebpackPlugin ({
          template: './public/index.html'
        })
      ]
  }
```

Write some scripts in package.json

```json
"scripts": {
    "serve": "webpack serve --mode=development",
    "build": "webpack build --mode=production"
  }
```

Add Function in main.js

```js

function init(){
    const = document.getElementById('upload')
    const fileReader = new FileReader()
    fileReader.onloadend = () => {
        let base64 = fileReader.result.replace(
          /^data:image\/(png|jpeg|jpg);base64,/ , ''
        )
        console.log(input.files[0])
        console.log(base64)
      }
    input.addEventListener('change',()=>{
      fileReader.reasAsDataURL(input.file[0])
    })
  }

init()
```

Install WASM Pack for webpack

```sh
npm install -D @wasm-tool/wasm-pack-plugin
```

Add some configuration to webpack.config.js

```js
const path = require('path')
const HTMLWEbpackPlugin = require('html-webpack-plugin')
const WasmPackPlugin = require('@wasm-tool/wasm-pack-plugin')

module.exports = {
    entry: './public/main.js',
    output: {
        path=path.resolve(__dirname, 'dist'),
        filename= 'index.js'
      },
      plugins: [
      new HTMLWebpackPlugin ({
          template: './public/index.html'
        }),
        new WasmPackPlugin({
            crateDirectory: path.resolve(__dirname, (.)
        })
      ]
  }
```

Add crate libary to your toml file.

```toml

[package]
name = "WASM"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"]

[dependencies]

```

Start your dev Server

```sh
npm run serve
```

Add your WASM Brigde to your .toml file

```toml
[package]
name = "WASM"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"]

[dependencies]
wasm-bindgen ="0.2.76"
```

Add RustApp to your main.js

```js
let rustApp = null
try{
rustApp = await import('../pkg')
}catch(e){
console.error(e)
return
}

console.log(rustApp)

function init(){
    const = document.getElementById('upload')
    const fileReader = new FileReader()
    fileReader.onloadend = () => {
        let base64 = fileReader.result.replace(
          /^data:image\/(png|jpeg|jpg);base64,/ , ''
        )
        console.log(input.files[0])
        console.log(base64)
      }
    input.addEventListener('change',()=>{
      fileReader.reasAsDataURL(input.file[0])
    })
  }

init()
```

Add asyncWebAssembly to your webpack.config.js

```js
const path = require('path')
const HTMLWEbpackPlugin = require('html-webpack-plugin')
const WasmPackPlugin = require('@wasm-tool/wasm-pack-plugin')

module.exports = {
    entry: './public/main.js',
    output: {
        path=path.resolve(__dirname, 'dist'),
        filename= 'index.js'
      },
      plugins: [
      new HTMLWebpackPlugin ({
          template: './public/index.html'
        }),
        new WasmPackPlugin({
            crateDirectory: path.resolve(__dirname, (.)
        })
      ],
      experiments: {
          asyncWebAssembly: true
      }
  }
```

Delete your console.log add and readAsDataURL tor your main.js

```js
let rustApp = null
try{
rustApp = await import('../pkg')
}catch(e){
console.error(e)
return
}

console.log(rustApp)

function init(){
    const = document.getElementById('upload')
    const fileReader = new FileReader()
    fileReader.onloadend = () => {
        let base64 = fileReader.result.replace(
          /^data:image\/(png|jpeg|jpg);base64,/ , ''
        )
        rustApp.grayscale(base64)
      }
    input.addEventListener('change',()=>{
      fileReader.readAsDataURL(input.file[0])
    })
  }

init()
```

Add a public Function with wasm_bindgen to your lib.rs

```rs
use wasm_bindgen::prelude::wasm_bindgen;

#[wasm_bindgen]
pub fn grayscale(encoded_file: &str){

  }
```

Install web-sys to enable console.log in Rust in your cargo.toml

```toml
[package]
name = "WASM"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"]

[dependencies]
wasm-bindgen ="0.2.76"

[dependencies.web-sys]
version = "0.3.4"
features = ["console"]
```

Add log function in your Rust App

```rs
use wasm_bindgen::prelude::wasm_bindgen;
use web_sys::console::log_1;

#[wasm_bindgen]
pub fn grayscale(encoded_file: &str){
    log(&encoded_file.into());
}
```

# 🦖🦖🦖🦖

````
__        __    _ _        __        ___    ____  __  __
\ \      / / __(_) |_ ___  \ \      / / \  / ___||  \/  |
 \ \ /\ / / '__| | __/ _ \  \ \ /\ / / _ \ \___ \| |\/| |
  \ V  V /| |  | | ||  __/   \ V  V / ___ \ ___) | |  | |
   \_/\_/ |_|  |_|\__\___|    \_/\_/_/   \_\____/|_|  |_|

 __  __           _       _
|  \/  | ___   __| |_   _| | ___
| |\/| |/ _ \ / _` | | | | |/ _ \
| |  | | (_) | (_| | |_| | |  __/
|_|  |_|\___/ \__,_|\__,_|_|\___|

```
````
