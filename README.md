# draka-blog

Welcome to my static website repository! This website contains a brief about page and a blog which documents my journey of setting up and managing a home network and self-hosted services.

The website is built using **Hexo** and styled with the **Cactus theme**. It includes posts on various topics such as network design, security, self-hosting guides, and more.

## How to Run Locally

If you'd like to view this blog on your own machine, follow the steps below to run it locally using Hexo.

### Prerequisites

Make sure you have the following installed:
- [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)
- [Hexo](https://hexo.io/)
  
### Steps

1. Clone this repository:
    ```bash
    git clone https://github.com/draka15/draka-blog.git
    ```

2. Navigate to the project directory:
    ```bash
    cd draka-blog
    ```

3. Install the necessary dependencies:
    ```bash
    npm install
    ```
4. Generate the static files:
    ```bash
    hexo generate
    ```

5. Start the local development server:
    ```bash
    hexo server
    ```

6. Visit `http://localhost:4000` in your browser to view the site locally.

### Create a New Page

You can create a new page by running:
    ```
    hexo new page <title>
    ```
If you want to create a new post run:
    ```bash
    hexo new post <title>
    ```

Then, you can edit the content of the blog post by editing the generated file in `source/_posts/` directory.
On the frontmatter you can add categories and tags.

Then you can generate the static files:
    ```bash
    hexo generate
    ```

Run the server locally
    ```bash
    hexo server
    ```
When everything is fine, deploy it on github pages
    ```bash
    hexo deploy
    ```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
