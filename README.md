### Data model
  - The site has many categories and tags
  - The site has many authors
  - An author has many books
  - A book can have many posts (book)
    - many quotes
    - many summary
    - many videos
  - All contents are posts
    - A post has one of the types: quote, video, article
    - A post can have tags, categories
    - A post can be about an author
    - A post can be about a book

### Command

`gcloud auth login`

`bundle exec jekyll build`

`gcloud config set project jekyll-content-site`

`gsutil rsync -Ri _site/ gs://www.alkchen.com`

###
  - [Adding a CNAME record](https://cloud.google.com/identity/docs/add-cname?hl=en_US)
  - [Host a static website](https://cloud.google.com/storage/docs/hosting-static-website)
  - [Make data public](https://cloud.google.com/storage/docs/access-control/making-data-public)
  - [Hosting a static website on Google Cloud using Google Cloud Storage](https://medium.com/google-cloud/hosting-a-static-website-on-google-cloud-using-google-cloud-storage-ddebcdcc8d5b)

### Reference
  - [Jekyll Codex](https://jekyllcodex.org/)
  - [Markdown cheatsheet](https://www.markdownguide.org/cheat-sheet/)
  - [Liquid Template](https://shopify.github.io/liquid)
  - [Liquid Doc](https://shopify.dev/api/liquid)
  - [Jekyll Generators](https://jekyllrb.com/docs/plugins/generators/)
  - [Bootstrap 5.0](https://getbootstrap.com/docs/5.0/)
  - [CSS colors](https://www.w3schools.com/cssref/css_colors.asp)


### Images
  - https://wallpapercave.com/
  - https://wallup.net/

### summaries 
  - https://www.samuelthomasdavies.com/
  - https://www.shortform.com/
  - https://fourminutebooks.com/book-summaries/
  - https://zeroavatar.com/category/book-summaries/
  - https://tylerdevries.com/book-summaries/
  - https://theartofliving.com/book-summaries/
  - https://ashishb.net/books-worth-reading/
  - https://booksconcepts.com/
  - https://growth.me/books/
  - https://www.hustleescape.com/lifelong-learning/
  - https://jamesclear.com/book-summaries