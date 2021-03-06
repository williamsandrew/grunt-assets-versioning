# grunt-assets-versioning

> Versioning static assets with Grunt

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-assets-versioning --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-assets-versioning');
```

## The "assets_versioning" task

### Overview
In your project's Gruntfile, add a section named `assets_versioning` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  assets_versioning: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      multitask: 'uglify'
    },
  },
})
```

### Options

#### options.use
Type: `String`
Possible values: `date`, `hash`
Default value: `date'

Should the revision marker be a md5 hash or a date ?

#### options.dateFormat
Type: `String`
Default value: `YYYYMMDDHHmmss'


If you choose to version your files using a date, you can specify a
dateformat. grunt-assets-versioning is using moment.js to format date.

#### options.dateStart
Type: `Date` or `Boolean`
Default value: `false'

Only works if you choose to version your files using a date.
Only files older than the dateStart will be versioned.
If set to true, all files will be versioned.

#### options.hashLength
Type: `Integer`
Default value: `8'

If you choose to version your files using a hash, hashLength let you set how
long the hash is going to be.

#### options.multitask
Type: `String` or `Boolean`
Default value: `false'

#### options.multitaskTarget
Type: `String`
Default value: The target name

#### options.skipExisting
Type: `Boolean`
Default value: `false`


### Usage Examples

#### Versioning using a date
In this example, dest.bundle.js is going to be versioned with a date, using
the default format YYYYMMDDHHmmss. The newest modification dates of all src files is
going to be used to create this timestamp. The generated result should be
dest/bundle.20130413004500.js

```js
grunt.initConfig({
  assets_versioning: {
    options: {
      use: 'date',
    },
    files: {
      'dest/bundle.js': ['src/file1.js', 'src/file2.js'],
    },
  },
})
```

#### Versioning using a hash
In this example, dest.bundle.js is going to be versioned with a hash. All sources files are going to be hashed and those hashes are also going to be hashed. The generated result should be
dest/bundle.2j4h2k.js

```js
grunt.initConfig({
  assets_versioning: {
    options: {
      use: 'hash',
      hashLength: 6,
    },
    files: {
      'dest/bundle.js': ['src/file1.js', 'src/file2.js'],
    },
  },
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
_(Nothing yet)_
