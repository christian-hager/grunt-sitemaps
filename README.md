# grunt-sitemaps

> A Grunt plugin to automate the creation of sitemaps

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-sitemaps --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-sitemaps');
```

## The "sitemaps" task

### Overview
In your project's Gruntfile, add a section named `sitemaps` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
    sitemaps: {
      default:{
        options: {
          baseUrl: 'http://www.mysite.com/',
          contentRoot: 'content/'
        },
        files: [{
          expand: true, // Enable dynamic expansion
          cwd: 'content/',
          src: ['**/*.{php,html}', '!exclude/**'] // Actual patterns to match
        }]
      }
    },
});
```

### Options

#### options.baseUrl
Type: `String`
Default value: `undefined`

A string value containing the base url of your site, e.g. 'http://www.mysite.com/'.

#### options.contentRoot
Type: `String`
Default value: `'.'`

A string value that contains the folder to be indexed.

#### options.dest
Type: `String`
Default value: `'.'`

A string value that contains the destination folder the generated sitemap will be written to.

#### options.removeFileExtensions
Type: `Boolean`
Default value: `'false'`

Set this to true if you want the generator to remove file extensions in urls.

#### options.mapIndexFilesToFolders
Type: `Boolean`
Default value: `'true'`

Set this to false if you don't want the generator to replace index files with their corresponding folders.

### Usage Examples

#### Default Options
In this example, the default options are used to index all html pages in folder content and write the generated sitemap to dist/sitemap.xml.

```js
grunt.initConfig({
    sitemaps: {
      options: {
        baseUrl: 'http://www.mysite.com/',
        contentRoot: 'content/',
        dest: 'dist/'
      },
      files: [{
        expand: true,
        cwd: 'content/',
        src: '**/*.html'
      }]
    }
});
```

#### Custom Options
In this example, custom options are used to do index all html pages in folder content and write the generated sitemap to dist/sitemap.xml.

```js
grunt.initConfig({
  sitemaps: {
    options: {
      baseUrl: 'http://www.mysite.com/',
      contentRoot: 'content/',
      dest: 'dist/',
      removeFileExtensions:true,
      mapIndexFilesToFolders: false
    },
    files: [{
      expand: true,
      cwd: 'content/',
      src: ['**/*.{php,html}', '!exclude/**']
    }]
  },
});
```

#### Page Priorities
Specifying page priorities can be done by matching the URL's absolute path to its priority. Non-matching pages use the default priority.

```js
grunt.initConfig({
  sitemaps: {
    options: {
      priority: '0.6',
      priorities: {
        '/': '1.0',
        '/about-us': '0.8'
      }
    }
  },
});
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History

 * 2016-03-02   v0.1.2   Support page priorities.
 * 2014-11-15   v0.1.0   Initial release.
