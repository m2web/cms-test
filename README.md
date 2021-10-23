# Netlify CMS  

from <https://www.netlifycms.org/docs/add-to-your-site/>

This Hugo site uses the Ava theme at <https://themes.gohugo.io/themes/hugo-theme-ava/>.

```bash
git submodule add https://github.com/jmau111/hugo-theme-ava.git themes/hugo-theme-ava
git submodule init
git submodule update
cp -a themes/hugo-theme-ava/exampleSite/. .
```

## App File Structure

A static admin folder contains all Netlify CMS files, stored at the root of your published site.  

|These generators |store static files in    |
|-------------------------------------------|-------------------------|
|Jekyll, GitBook |/ (project root)         |
|Hugo, Gatsby, Nuxt, Gridsome, Zola, Sapper|/static                  |

Inside the admin folder, you'll create two files:

```git
admin
 ├ index.html
 └ config.yml
```

On the code side, `/admin/index`, is a basic HTML starter page that loads the Netlify CMS JavaScript file. The second file, `/admin/config.yml`, is the heart of your Netlify CMS installation, and a bit more complex. 

## Index

`/admin/index.html`

The first file, admin/index.html, is the entry point for the Netlify CMS admin interface. This means that users navigate to yoursite.com/admin/ to access it. 

In this example, we pull the admin/index.html file from a public CDN:

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Content Manager</title>
</head>
<body>
  <!-- Include the script that builds the page and powers Netlify CMS -->
  <script src="https://unpkg.com/netlify-cms@^2.0.0/dist/netlify-cms.js"></script>
</body>
</html>
```

In the code above the script is loaded from the unpkg CDN. Should there be any issue, jsDelivr can be used as an alternative source. Simply set the src to https://cdn.jsdelivr.net/npm/netlify-cms@^2.0.0/dist/netlify-cms.js

## Configuration

`/admin/config`

Configuration is different for every site, so we'll break it down into parts. Add all the code snippets in this section to your admin/config.yml file.

### Backend

We're using Netlify for our hosting and authentication in this tutorial, so backend configuration is fairly straightforward.

For GitHub and GitLab repositories, you can start your Netlify CMS config.yml file with these lines:

```yml
backend:
  name: git-gateway
  branch: main # Branch to update (optional; defaults to main)
```

**Editorial Workflow**  
Note: Editorial workflow works with GitHub repositories, and support for GitLab and Bitbucket is in beta.

By default, saving a post in the CMS interface pushes a commit directly to the publication branch specified in backend. However, you also have the option to enable the Editorial Workflow, which adds an interface for drafting, reviewing, and approving posts. To do this, add the following line to your Netlify CMS config.yml:

*This line should NOT be indented*

```yml
publish_mode: editorial_workflow  
```

### Media and Public Folders
Netlify CMS allows users to upload images directly within the editor. For this to work, the CMS needs to know where to save them. If you already have an images folder in your project, you could use its path, possibly creating an uploads sub-folder, for example:

*This line should NOT be indented*  

```yml
media_folder: "images/uploads" # Media files will be stored in the repo under images/uploads
```

If you're creating a new folder for uploaded media, you'll need to know where your static site generator expects static files. You can refer to the paths outlined above in App File Structure, and put your media folder in the same location where you put the admin folder.

Note that the media_folder file path is relative to the project root, so the example above would work for Jekyll, GitBook, or any other generator that stores static files at the project root. However, it would not work for Hugo, Hexo, Middleman or others that store static files in a subfolder. Here's an example that could work for a Hugo site:

*This line should NOT be indented*  

```yml
media_folder: "static/images/uploads" # Media files will be stored in the repo under static/images/uploads
public_folder: "/images/uploads" # The src attribute for uploaded media will begin with /images/uploads
```

The configuration above adds a new setting, public_folder. While media_folder specifies where uploaded files are saved in the repo, public_folder indicates where they are found in the published site. Image src attributes use this path, which is relative to the file where it's called. For this reason, we usually start the path at the site root, using the opening `/`.

If public_folder is not set, Netlify CMS defaults to the same value as media_folder, adding an opening / if one is not included.

### Collections

Collections define the structure for the different content types on your static site. Since every site is different, the collections settings differ greatly from one site to the next. Let's say your site has a blog, with the posts stored in `_posts/blog` (such as the case for `Jekyll`), and files saved in a date-title format, like 1999-12-31-lets-party.md.  

So:  
-where the content is stored determines your collections:folder value  
-how you name your content files determines your collections:slug

Now you need to update the config.yml file. I use Github and my deploy branch is main:  
(see <https://www.kevinsahin.com/blog/adding-netlify-cms-to-an-existing-hugo-website/>):

```yml
backend:
  name: git-gateway
  branch: main # Branch to update (optional; defaults to main)

# This line should NOT be indented
publish_mode: editorial_workflow

# These line should NOT be indented
media_folder: "static/images/uploads" # Media files will be stored in the repo under static/images/uploads
public_folder: "/images/uploads" # The src attribute for uploaded media will begin with /images/uploads

collections:
  - name: "blog"
    label: "Blog"
    folder: "content/blog"
    create: true
    fields:
      - { label: "Title", name: "title", widget: "string" }
      - { label: "Date", name: "date", widget: "date" }
      - { label: "Body", name: "body", widget: "markdown" }
      - { label: "Featured Image", name: "image", widget: "image"}
      - { label: "Description", name: "description", widget: "string"}
```

The collections part is the most important one that you will need to adapt.

Collections represent how our content is structured. Generally you have one or several fields in your Front-matter, in my case title, date, image and description.
Be careful about the folder value, in my case it's `content/blog` because my hugo theme works this way, but the default value for Hugo is `content/posts`.
