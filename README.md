# multerDemo
## How to use

- Clone the project 
- install npm
- Create a folder uploads

```
// import packages
const express = require('express');
    const multer  = require('multer');

//Set Storage
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

//Create express app
const app = express()

//Upload file
app.post('/uploadDemo', upload.array('manyFiles'), function (req, res, next) {
    res.send('File uploaded please check /public/uploads folder')
})

app.listen(3000);
```
