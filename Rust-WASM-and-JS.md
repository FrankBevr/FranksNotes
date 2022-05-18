# 🦖 Rust-WASM-and-JS 

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

      ▶ Testing

      ▶ Outro & chitchat


# 🦖🦖 Quick Intro

```
 / _ \ _   _(_) ___| | __ |_ _|_ __ | |_ _ __ ___  
| | | | | | | |/ __| |/ /  | || '_ \| __| '__/ _ \ 
| |_| | |_| | | (__|   <   | || | | | |_| | | (_) |
 \__\_\\__,_|_|\___|_|\_\ |___|_| |_|\__|_|  \___/ 
                                                   
```

# 🦖🦖🦖 Set Up

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
module.exports = {

}
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
<html>
  <head>
    <meta charset="utf-8">
    <title>Image Effects</title>
    <link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">
    <style>
      h1 {
        font-family: 'Pacifico', cursive;
      }

      .bg {
        animation: slide 3s ease-in-out infinite alternate;
        background-image: linear-gradient(-60deg, #ACFFAD 50%, #50CB93 50%);
      }

      .bg:nth-child(2) {
        animation-direction:alternate-reverse;
        animation-duration:4s;
      }
      
      .bg:nth-child(3) {
        animation-duration:5s;
      }

      @keyframes slide {
        0% {
          transform:translateX(-25%);
        }
        100% {
          transform:translateX(25%);
        }
      }
    </style>
  </head>
  <body>
    <div class="bg fixed inset-y-0 -inset-x-2/4 opacity-50 z-0 bg-gradient-to-r from-yellow-400 to-pink-500"></div>
    <div class="bg fixed inset-y-0 -inset-x-2/4 opacity-50 z-0 bg-gradient-to-r from-yellow-400 to-pink-500"></div>
    <div class="bg fixed inset-y-0 -inset-x-2/4 opacity-50 z-0 bg-gradient-to-r from-yellow-400 to-pink-500"></div>
    <div class="flex items-center justify-center h-screen relative z-100">
    
      <div class="bg-white bg-opacity-95 border shadow-lg p-10 text-center max-w-2xl">
        <h1 class="text-5xl mb-8">Image Effects</h1>
        <p class="mb-4">Need to do some basic image manipulation? Just upload your image below. We'll take care of the rest.</p>
        <label class="bg-pink-600	text-white w-full p-6 block cursor-pointer font-bold mb-4">
          <!-- File Input -->
          <input type="file" id="upload" accept=".png" class="hidden">
          Upload PNG Image
        </label>
        <!-- Image -->
        <img id="new-img" class="w-auto mx-auto">
      </div>
      
    </div>
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

# 🦖🦖🦖🦖 Write WASM Module

```
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
Add base64 to your cargo.toml
```toml
[package]
name = "WASM"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"]

[dependencies]
wasm-bindgen ="0.2.76"
base64 = "0.13.0"

[dependencies.web-sys]
version = "0.3.4"
features = ["console"]
```

Use it in lib.rs
```rs
use wasm_bindgen::prelude::wasm_bindgen;
use web_sys::console::log_1;
use base64::decode;

#[wasm_bindgen]
pub fn grayscale(encoded_file: &str){
    log(&encoded_file.into());
    log(&"Grayscale called".into());

    let base64_to_vector = decode(encoded_file).unwrap();
    log(&"Image decoded".into())
}
```

Test an Image and look into your console.

Add image crate into your cargo.toml
```toml
[package]
name = "WASM"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"]

[dependencies]
wasm-bindgen ="0.2.76"
base64 = "0.13.0"
image ="0.23.14"

[dependencies.web-sys]
version = "0.3.4"
features = ["console"]
```

Add image and use image in your lib.rs
```rs
use wasm_bindgen::prelude::wasm_bindgen;
use web_sys::console::log_1;
use base64::decode;
use image::loag_from_memory;

#[wasm_bindgen]
pub fn grayscale(encoded_file: &str){
    log(&encoded_file.into());
    log(&"Grayscale called".into());

    let base64_to_vector = decode(encoded_file).unwrap();
    log(&"Image decoded".into())

    let img = load_from_memory(&base_to_vector.unwrap());
    log(&"Image loaded".into())
}
```

Apply Grayscale in your lib.rs
```rs
use wasm_bindgen::prelude::wasm_bindgen;
use web_sys::console::log_1;
use base64::decode;
use image::loag_from_memory;

#[wasm_bindgen]
pub fn grayscale(encoded_file: &str){
    log(&encoded_file.into());
    log(&"Grayscale called".into());

    let base64_to_vector = decode(encoded_file).unwrap();
    log(&"Image decoded".into())

    let mut img = load_from_memory(&base_to_vector.unwrap());
    log(&"Image loaded".into())

    img = img.grayscale();
    log(&"Grayscale effect applied".into());
}
```

load into Buffer in your lib.rs
```rs
use wasm_bindgen::prelude::wasm_bindgen;
use web_sys::console::log_1;
use base64::decode;
use image::loag_from_memory;
use image::IMageOutputFormat::Png;

#[wasm_bindgen]
pub fn grayscale(encoded_file: &str){
    log(&encoded_file.into());
    log(&"Grayscale called".into());

    let base64_to_vector = decode(encoded_file).unwrap();
    log(&"Image decoded".into())

    let mut img = load_from_memory(&base_to_vector.unwrap());
    log(&"Image loaded".into())

    img = img.grayscale();
    log(&"Grayscale effect applied".into());

    let mut buffer= vec![];
    img.write_to(&mut buffer,Png).unwrap();
    log(&"New image written".into());
}
```

Javascript
File --> Base64

Rust
Base64 --> Binary --> DynamicImage --> Binary -->Base64

Javscript 
Base64 --> File


Encoding Image
```rs
use wasm_bindgen::prelude::wasm_bindgen;
use web_sys::console::log_1;
use base64::{encode, decode};
use image::loag_from_memory;
use image::IMageOutputFormat::Png;

#[wasm_bindgen]
pub fn grayscale(encoded_file: &str) -> String{
    log(&encoded_file.into());
    log(&"Grayscale called".into());

    let base64_to_vector = decode(encoded_file).unwrap();
    log(&"Image decoded".into())

    let mut img = load_from_memory(&base_to_vector.unwrap());
    log(&"Image loaded".into())

    img = img.grayscale();
    log(&"Grayscale effect applied".into());

    let mut buffer= vec![];
    img.write_to(&mut buffer,Png).unwrap();
    log(&"New image written".into());

    let encoded_image = encode(&buffer);
    let data_url = format!(
    "data:image/png;base64,{}",
    encoded_image
    );

    data_url
}
```

Output your converted image through JS in main.js
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
        let img_data_url = rustApp.grayscale(base64)
        document.getElementById('new-img').setAttribute('src', img_data_url)
      }
    input.addEventListener('change',()=>{
      fileReader.readAsDataURL(input.file[0])
    })
  }

init()
```

# 🦖🦖🦖🦖🦖 Testing
```
 _____         _   _             
|_   _|__  ___| |_(_)_ __   __ _ 
  | |/ _ \/ __| __| | '_ \ / _` |
  | |  __/\__ \ |_| | | | | (_| |
  |_|\___||___/\__|_|_| |_|\__, |
                           |___/ 
```

Take a small Image and convert it into a Grayscale Image

🚀🎩 Whooolaaa 🎩🚀

# 🦖🦖🦖🦖🦖🦖 ChitChat

```
  ____ _     _ _    ____ _           _   
 / ___| |__ (_) |_ / ___| |__   __ _| |_ 
| |   | '_ \| | __| |   | '_ \ / _` | __|
| |___| | | | | |_| |___| | | | (_| | |_ 
 \____|_| |_|_|\__|\____|_| |_|\__,_|\__|
```
                                         
