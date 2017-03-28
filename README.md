# Static Documentation and Github

## Github Pages 

 * Ability to host any static files in a github repository. 
 * Similar to S3 but free
 * Several Options:
   * Use `gh-pages` branch 
   * Use `master` branch 
   * Use `docs` directory on `master` branch
* URL format is: 
  ```
  https://<username or organization>.github.io/<project name>
  ```
* Allowed to have custom domain easily - just point your DNS
* Can put stuff at 
  ```https://<username or organization>.github.io/
  ```
  by creating a project named after the organization or user.
  
## Basics

### Markdown
 * Defacto Standard
 * But not really standardized (e.g. Github-flavored Markdown)
 * Learn it
 * Quick Examples
   * [https://jbt.github.io/markdown-editor/](https://jbt.github.io/markdown-editor/)
   * [https://stackedit.io/editor](https://stackedit.io/editor)

#### Editors
 * [https://jbt.github.io/markdown-editor/](https://jbt.github.io/markdown-editor/)
 * [https://stackedit.io/editor](https://stackedit.io/editor)
 * [Macdown](https://macdown.uranusjr.com/)
 * [VSCode](https://code.visualstudio.com/)
 * Plugins for Sublime, etc
 * Infinite others

## Approaches

 1. Write Markdown source, compile/build it, upload HTML
 2. Write Markdown source, upload raw, have JS render on the fly
   1. [Some critical of this approach](http://stackoverflow.com/questions/22793883/parse-markdown-on-the-fly)
   2. Only found one realistic framework that is a bit old: [Flatdoc](http://ricostacruz.com/flatdoc/#flatdoc)
     * [https://edgarroman.github.io/doctest-flatdoc/](https://edgarroman.github.io/doctest-flatdoc/)

Will be focusing on **option 1 above**

### How it works (option 1)

One-time setup of github pages (Easiest to create the `gh-pages` branch.  Autodetected by github).  Then:

 1. Write source material in markdown
 2. Check source material into the `master` branch
 3. Run a build on the source material to render material
 4. Check in rendered material into the `gh-pages` branch
 5. Rinse, Repeat

If you're really cool, then you will have a CI system do your build for you.  But if you're cheap (like me), just do it manually (Lazy!  SAD!)

## Frameworks

**Tons** Pretty good list: [https://www.staticgen.com/](https://www.staticgen.com/)

Pretty much any language you want: Python, .NET, Go, PHP - even non languages like Javascript!

 * Some are better for blogs: Have fancy tag clouds and 'most recent' widgets
 * Some are just straight up pages: More general documentation
 * Some are focused on API: But swagger would probably be a better choice

### Criteria for this talk

 1. General Static Page (non-blog)
 2. Minimal install overhead (e.g. only Python)
 5. Good Documentation
 3. Reasonably good looking output
 4. Simple

### Best frameworks

 1. [mkdocs](http://www.mkdocs.org/)

Others:

 * [Cactus](https://github.com/eudicots/Cactus) - Bad docs
 * [Sphinx](http://www.sphinx-doc.org/en/stable/index.html) - Complicated
 * [Gitbook](https://www.gitbook.com/) - Corporate pig dogs
 * [Jekyll](https://jekyllrb.com/) - Don't know how to use ruby
 * [Hyde](http://hyde.github.io) - Terrible documentation
 
## MKDocs Walkthrough

1. Create Repo
2. Install mkdocs
	```
	virtualenv ve
	source ve/bin/activate
	pip install mkdocs
	```
3. Init the mkdocs project
	```
	mkdocs new .
	```
4. Customize mkdocs.yml
   ```
   site_name: Mkdocs overview
   pages:
     - Home: 'README.md'
   ```
5. Add / Edit pages
6. Run local server
   ```
   mkdocs serve
   ```
7. Edit and revise
8. Commit and push source to github
9. Deploy to gh-pages
   ```
   mkdocs gh-deploy
   ```
10. Profit


## Advanced

### Themes

   ```
   site_name: Mkdocs overview
   pages:
     - Home: 'README.md'
   theme: readthedocs
   ```

### Extensions

* Any pyMdown extensions
  ```
  pip install pymdown-extensions
  ```
  
* [http://facelessuser.github.io/pymdown-extensions/](http://facelessuser.github.io/pymdown-extensions/)

   ```
   site_name: Mkdocs overview
   pages:
     - Home: 'README.md'
   markdown_extensions:
     - pymdownx.superfences
   ```























