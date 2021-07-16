# How to use this Theme

###  What is this 
This is the github based documentation project. It works on top of Markdown. Basically, we will write content in markdown and github will render it as static documentation pages. 

### How to add a document ? 
All documents should go inside one of the folders in the _docs folder. Each folder here is a topic. If there aren't any topic available run `sh .gen-topic` command from root directory to create a topic. Then add documents under the topic.

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
### How to commit the document 

* Run `sh .gen-toc` from the root folder of the repository. This will make sure that your document is searchable by keyword and it will appear in the document index on the left hand side of the page.
* Commit the file
* Push it to github. and see your document. 

### How to modify an existing page ? 
* Open an existing document.
* Modify it
* Run `sh .gen-toc` from the root folder of the repository.
* Commit it 
* Push the commit.
* View it in github.

> Note: You can also edit document in github, if the metadata section is not changing.

### Help on writing the content 

* Refer to kramdown / markdown syntax. 
* When referring to images or other assets within repository use the following URL syntax `![]({{ '/<relative_path_from_root_dir>' | relative_path }})`. Using this syntax will make sure the images are loaded properly in any hosting environment.

## Advanced

You an also setup documentation locally and use it. There are lot of advantages in doing so. You can validate before pushing it to public. To run the documentation locally and view it, here are the following steps.

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

### Using Jekyll Admin console for editing
* After completing the above step, run `localhost:5000/admin`
* You should be able to see a admin console that will help you to create / modify pages and metadata easily.
