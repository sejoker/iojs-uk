# ua.iojs.org

Jekyll is, at its core, a text transformation engine.
The concept behind the system is this: you give it text written in your favorite markup language, be that Markdown, Textile, or just plain HTML, and it churns that through a layout or series of layout files.
Throughout that process you can tweak how you want the site URLs to look, what data gets displayed in the layout, and more.
This is all done through editing text files, and the static web site is the final product.

A basic Jekyll site usually looks something like this:

```bash
.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
└── index.html
```

An overview of what each of these does:

+ **_config.yml** stores configuration data. Many of these options can be specified from the command line executable but it’s easier to specify them here so you don’t have to remember them;

+ **_drafts** are unpublished posts. The format of these files is without a date: ```title.md```.

+ **_includes** - these are the partials that can be mixed and matched by your layouts and posts to facilitate reuse. The liquid tag ```{% raw %}{% include file.ext %}{% endraw %}``` can be used to include the partial in ```_includes/file.ext```.

+ **_layouts** - these are the templates that wrap posts. Layouts are chosen on a post-by-post basis in the YAML Front Matter. The liquid tag ```{% raw %}{{ content }}{% endraw %}``` is used to inject content into the web page.

+ **_posts** - your dynamic content, so to speak. The naming convention of these files is important, and must follow the format: ```YEAR-MONTH-DAY-title.md```. The permalinks can be customized for each post, but the date and markup language are determined solely by the file name.

+ **_data** - well-formatted site data should be placed here. The jekyll engine will autoload all yaml files (ends with ```.yml``` or ```.yaml```) in this directory. If there's a file ```members.yml``` under the directory, then you can access contents of the file through ```site.data.members```.

+ **_site** - this is where the generated site will be placed (by default) once Jekyll is done transforming it. It’s probably a good idea to add this to your ```.gitignore``` file.

+ **index.html** and other HTML, Markdown, Textile files provided that the file has a YAML Front Matter section, it will be transformed by Jekyll. The same will happen for any ```.html```, ```.markdown```, ```.md```, or ```.textile``` file in your site’s root directory or directories not listed above.

+ Other Files/Folders - every other directory and file except for those listed above—such as ```css``` and ```images``` folders, ```favicon.ico``` files, and so forth—will be copied verbatim to the generated site.
