# File Interaction with Node

By the end of this lesson, you should be able to read, write, and update files with NodeJS.

## Core Learning Objective

*	Use NodeJS APIs to interact with files and the web

## Sub-Objectives

* Define CRUD
* Read from files
* Overwrite files
* Programmatically update files

### Prereqs

Before starting this lesson, Fork & Clone this repository. Make sure that you can run `npm start` and that you get the following output:
```
Hello, Node!
```

### Instructions & Guiding Questions

- [ ] Begin by renaming `data/pets.sample.json` to `pets.json`

* **Question:** In this lesson we will be modifying the contents of the `pets.json` file. Why do you think that file appears inside of the `.gitignore` file?

**Your Answer:**
* Hidden files and git will ignore them.


- [ ] Take a look at the NodeJS documentation for the [fs module](https://nodejs.org/api/fs.html). When looking at documentation like this it can be overwhelming to start but you likely know more than you think. Take a moment to find a few concepts you understand.

---

- [ ] One of the most common patterns we'll come across as web developers is the concept of [CRUD](https://www.codecademy.com/articles/what-is-crud). Take a moment to define what CRUD represents.

* **Question:** Imagine you have a file called `classmates.txt`. For each part of CRUD, describe how the action would interact with the file.

**Your Answer:**
* Create classmates.txt, Read classmates.txt, Update, and/or Delete

- [ ] Consider the above and then look back through the [fs module](https://nodejs.org/api/fs.html) documentation.

* **Question:** What methods represent each CRUD action?

* **Your Answer:**
fs.readFileSync(path[, options]) fs.writeFileSync(file, data[, options])
fs.appendFile(path, data[, options], callback)
fs.copyFile(src, dest[, flags], callback)
---

- [ ] Take a look at the following two methods: [fs.readFile()](https://nodejs.org/api/fs.html#fs_fs_readfile_path_options_callback) and [fs.readFileSync()](https://nodejs.org/api/fs.html#fs_fs_readfilesync_path_options).

* **Question:** What is the difference between these two methods?

* **Your Answer:**
fs.readFile(path[, options], callback) has two options fs.readFileSync(path[, options]) has the one.  fs.readFile() reads the contents of a file where the fs.readFileSync() returns the contents of a path.  

---

- [ ] Take a look at [fs.writeFile()](https://nodejs.org/api/fs.html#fs_fs_writefile_file_data_options_callback) and [fs.appendFile()](https://nodejs.org/api/fs.html#fs_fs_appendfile_path_data_options_callback).

* **Question:** Describe the difference between these two methods.

* **Your Answer:**
fs.writeFile() will over write the current data and fs.appendFile() will add to the current contents.
---

- [ ] Imagine you want to edit the middle of a file. You can use the [fs module](https://nodejs.org/api/fs.html) and the JavaScript language.

* **Question:** How would you do so?

* **Your Answer:**
I would import the json and parse the data into a variable.  Use that variable to find index as key to which information I wish to manipulate.  Then convert back to json format and use fs methods to write back to the file.

---

- [ ] In Node, you'll have access to a global variable called `__dirname`. Add the following to your `index.js` file.
  ```js
  const path = require('path')
  const petsFile = path.join(__dirname, 'data', 'pets.json')
  ```

* **Question:** Describe what is happening in the above code.

* petsFile is a variable that will have the direct path to the pets.json file based on index.js relative path.  So the _dirname = data since data is the folder relative to index.js and pets.json is the file of the directory/name "data".  The join method is combining the directory path, folder name, and file name.

### Exercise

You now have the knowledge needed to edit files on your file system. **A note of caution:** this means you have the ability to delete files programmatically from your machine. That can be pretty dangerous! In this exercise and class, we will never be deleting any files programmatically. If you ever find yourself in a situation where you do need to do so, be careful.

For the rest of the time we have, use the knowledge you've gained to build functions that will modify data inside of the `pets.json` file. You should be able to **create** new pets, **read** information about all your pets, **update** a pet's information, and **delete** a pet from your records.

Assuming your `pets.json` starts with one pet like so:

```json
[
  {
    "name": "Meowser",
    "kind": "cat",
    "age": 3
  }
]
```

You should make the following functions and they should return the values that are commented out.

```js
console.log(read())
// [ { name: 'Meowser', kind: 'cat', age: 3 } ]

console.log(create('Duchess', 'bird', 2))
// [
//   { name: 'Meowser', kind: 'cat', age: 3 },
//   { name: 'Duchess', kind: 'bird', age: 2 }
// ]

console.log(create('Duchess', 'bird', 2))
// "Duchess" is already a pet!

console.log(remove('Snoopy'))
// No pet found by the name of "Snoopy"

console.log(remove('Duchess'))
// { name: 'Duchess', kind: 'bird', age: 2 }

console.log(read())
// [ { name: 'Meowser', kind: 'cat', age: 3 } ]

console.log(update('Duchess', 'bird', 3))
// No pet found by the name of "Duchess"

console.log(update('Meowser', 'cat', 4))
// { name: 'Meowser', kind: 'cat', age: 4 }

console.log(read())
// [ { name: 'Meowser', kind: 'cat', age: 4 } ]

console.log(update('Meowser', 'cat', 3))
// { name: 'Meowser', kind: 'cat', age: 3 }
```

#### Resources

* [NodeJS: File System](https://nodejs.org/api/fs.html)
* [Codecademy: What is CRUD?](https://www.codecademy.com/articles/what-is-crud)