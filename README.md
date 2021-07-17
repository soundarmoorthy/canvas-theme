# How to use this Theme

##  About
This is a jekyll theme that is useful if you want to write project documentation. This theme works well for hosting in github pages.

## Credits
This theme is based on [Docsy Jekyll](https://github.com/vsoch/docsy-jekyll). Apart from the extended features provided here, this is completely based on their work. Consider this attribution.

## Features
* All features of [Docsy Jekyll](https://github.com/vsoch/docsy-jekyll). 
* Auto generate topics and table of contents. No editing of of yaml files needed.
* Auto generated index pages for topics
* Support for authors for pages
* Privacy policy page
* Use fonts from google CDN, and support for changing them easily.

## How To 

### Branding
* You can edit the different information in `_config.yml` file in the root directory with your own branding information. Few important things
* Don't change baseurl. 
* Change the `url` entry to your github base url. If you are using public github instance, you can leave it. 
* Change the repo entry to the complete url to your github repository. It should look like "https://github.optum.com/<user>/<repo>
* Change the github_user to your github username. If you are using enterprise github use the organization name here.
* Change the github_repo to your github repository name
* Change the github_branch to your default branch that will serve the files. It should be either master or gh-pages, depending on your [repository settings](https://guides.github.com/features/pages/).

### Add a topic
All documents should go inside one of the folders in the _docs folder. Each folder here is a topic. If there aren't any topic available run `sh .gen-topic` command from root directory to create a topic. Then add documents under the topic. For simplicity there is a sample.md file created under each topic by default. You can start by editing the file to suit your needs.

### Add a document 
* Your documents should go into one of these folders. Write it in markdown format. 
* Add the metadata. You can use the following template to add new metadata to the documents. Note that the spaces and alignment are important.
    ```
    ---
    title: <title>
    category: <developer, ingress, egress, arch, process>
    authors:
    - <author1>
    - <author2>
    description: <A short description of the page>
    tags:
    - <tag1>
    - <tag2>
    ---
    ```

### Generate table of contents
* Run `sh .gen-toc` from the root folder of the repository. This will make sure that your document is appear in the index table on the left hand side of the page.

### How to modify an existing document
* Open an existing document.
* Modify it
* Run `sh .gen-toc` from the root folder of the repository.

> Note: You can also edit document in github itself, if the metadata section is not changing.

### Help on writing the content 

* Refer to [kramdown syntax](https://kramdown.gettalong.org/)
* When referring to images or other assets within repository use the following URL syntax `![]({{ '/<relative_path_from_root_dir>' | relative_path }})`. Note that the path should begin with a forward slash. Using this syntax will make sure the assets are loaded properly in any hosting environment.

### Update the logo 
* Replace the file <rootdir>/assets/images/logo.jpeg with your own image and use the same name.

### Use a different font
* As of now the fonts Inconsolata is used for monospace and `Raleway` is used for regular text from the Google CDN. If you want to update it, edit the /assets/css/main.css file. Modify the following lines with the apporpriate font you want to use

```
@import url('https://fonts.googleapis.com/css2?family=Inconsolata:wght@300&display=swap');

html * 
{
    font-family: 'Raleway' !important;
}

pre *
{
    font-family: 'Inconsolata' !important;
}
code *
{
    font-family: 'Inconsolata' !important;
}
```

## Setup locally

You an also setup documentation locally. There are lot of advantages in doing so. You can validate before pushing it to public. To run the documentation locally and view it, here are the following steps.

### Prerequisites
* Ruby 2.6 or later
> Note : If you have a Mac, it's most likely that you have ruby installed. From the command line type `ruby -v` and check it. 

### Steps to setup 
* Check if ruby is present. 
  ```
    ruby -v
  ```
* If not present, install Ruby.
  ```
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    brew install ruby
  ```    
* Clone the repository locally
  ```
  git clone https://github.com/<user>/<repo>.git
  cd <repo>
  ```

* Run the following command inside the repository directory.
  ```
    gem install bundler
    bundle install
  ```

### Running the server locally and verify the documents
* Run the following command. 
    ```
    bundle exec jekyll serve --baseurl="" --watch --verbose --port=5000
    ```
* Goto browser and type `localhost:5000`
* You can also use a different port if you like to.

### Using Jekyll Admin console for editing
* After completing the above step, run `localhost:5000/admin`
* You should be able to see a admin console that will help you to create / modify pages and metadata easily.
