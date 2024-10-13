# VTuber Button Starter

This is a template project designed to help developers quickly create a customizable VTuber soundboard website, allowing them to easily add their own voice recordings and modify the site as needed.

## Table of Contents

- [How to use this template](How-to-use-this-template)
  - [Create a repository from the template](#create-a-repository-from-the-template)
  - [Clone locally](#clone-locally)
  - [Modify the configuration](#modify-the-configuration)
    - [Site configuration](#site-configuration)
    - [Appearance and styles](#appearance-and-styles)
  - [Add your own audio files](#add-your-own-audio-files)
  - [Local development and debugging](#local-development-and-debugging)
  - [Deployment](#deployment)
- [Contributing to This Project](#contributing-to-this-project)
- [License](#license)
- [Credits](#credits)

## How to use this template

### Create a repository from the template

1. Click the "Use this template" button on the GitHub page for this repository.
2. Fill in the repository name (e.g. `miel-noises`) and description.
3. Choose whether to make the repository public or private.
4. Click "Create repository from template".

### Clone locally

Clone your newly created repository locally using Git:

```sh
git clone https://github.com/<your-username>/<repository-name>
```

### Modify the configuration

Open the cloned directory in your preferred editor/IDE, then modify the following files:

#### Site configuration

Edit the config file located in `src/site-config.ts` to change the site title, description, GitHub repository URL, and other settings.

#### Appearance and styles

The project uses a CSS reset in `src/styles/reset.css` (which is imported in `src/main.ts`) to standardize styling across browsers, and additional styling can be modified in `src/App.svelte` and component-specific files within `src/lib/components`.

### Add your own audio files

The audio files should be in mp3 format, and it's recommended to use a 128Kbps bitrate to avoid bandwidth and network latency issues. Store the files in the `public/voices/` directory. Subdirectories are used for categories, and the corresponding URL will be `/voices/`.

All audio information is stored in `assets/voices.json`. To add or modify audio, you’ll also need to update this file.

The structure of `voices.json` is as follows: the outermost layer is an array called `categories`, which can contain several groups (categories). Each group should have a unique `name` and a list of audio files:

```json
{
  "name": "Category Name",
  "voiceList": [...]
}
```

Inside `voiceList`, you can include multiple audio clips. Each audio entry contains a unique name and the path relative to `public/voices/`.

```json
{
  "name": "Get some help",
  "path": "get_some_help.mp3"
}
```

Replace the content of `voices.json` with your own data. The template provides a reference structure that you can modify to suit your needs.

### Local Development and Debugging

This project uses the [Svelte](https://svelte.dev) framework. To set up the local development environment, first, install the latest version of [Node](https://nodejs.org).

1. Fork and clone the code to your local environment.
2. Navigate to the code directory and run `npm install` to install project dependencies.
3. Start the local development server by running `npm run dev`. This will start the server on `localhost:5173`. Any changes made to the code will be hot-reloaded and reflected in the browser.
4. To compile files for deployment, run `npm run build`. This will generate deployable files in the `dist/` directory, suitable for static website hosting like GitHub Pages.

### Deployment

After generating the static HTML files in the `dist/` directory using npm run build, you can deploy your site to various static hosting providers such as Netlify, Vercel, or GitHub Pages. For more information, refer to [Vite deployment documentation](https://vite.dev/guide/static-deploy.html).

## Contributing to This Project

If you have any suggestions, feel free to post them in [Issues](https://github.com/Pyrospower/vtuber-button-starter/issues).

If you would like to contribute code, please fork this project, make your changes, and submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Credits

- Frontend is written in [Svelte](https://svelte.dev) using [Vite](https://vite.dev) as the build tool.
- The CSS reset was made using [Modern CSS Reset](https://www.joshwcomeau.com/css/custom-css-reset) and some tricks showed in [Kevin Powell](https://youtube.com/kevinpowell)'s videos.
- CSS variables are used for theming, inspired by [shadcn/ui](https://ui.shadcn.com/themes).
- [Material Vtuber Button](https://github.com/lonelyion/material-vtuber-button), [VBUP](https://github.com/vbup-osc) and [IRySoundboard](https://irysoundboard.com) for inspiration.
