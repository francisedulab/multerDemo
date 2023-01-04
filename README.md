# Multer Demo

## How to use


- Clone the project 
- change directory and npm install
- Create a folder named public
- Inside public directory create one more folder named uploads
- Add the following code in app.js file

```sh
const express = require('express');                                                             // Importing Express
const multer  = require('multer');                                                              // Importing multer

const storage = multer.diskStorage({
    destination: function (req, file, cb) {
      cb(null, './public/uploads')
    },
    filename: function (req, file, cb) {
      const uniqueSuffix = Date.now() + '-' + Math.round(Math.random() * 1E9)
      cb(null, file.fieldname + '-' + uniqueSuffix + '.png')
    }
  })
  
  const upload = multer({ storage: storage })


const app = express()                                                                             // Creating instace of express

app.post('/uploadDemo', upload.array('manyFiles'), function (req, res, next) {                    // Creating post api to upload files
    res.send('File uploaded please check /public/uploads folder')
})

app.listen(3000);                                                                                  // Listening on port 3000

```
