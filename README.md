Presentation slides for the [neutronics-workshop](https://github.com/fusion-energy/neutronics-workshop)

# View the sides.

The slides are available in html and pdf format. With each release these two formats are automatically created and uploaded as an artifact to the release. Check out the latest slide release [here]().

# Develop the slides

## Install slidev

The slides are built using [sli.dev](https://sli.dev/) which can be installed with a npm command.

```bash
npm i -g @slidev/cli
```

clone the repo
git clone https://github.com/fusion-energy/neutronics-workshop-slides.git

navigate to the root folder of the repo

```bash
cd neutronics-workshop-slides
```

Launch slidev which will load up the slides on your local host
```bash/home/jshimwell/neutronics-workshop-slides/html
slidev
```

Navigate to your local host to see the slides
[http://localhost:3031](http://localhost:3031)

Make changes to the slides.md file and the slides will update in your browser

## Exporting the slides to PDF

This is automatically run by Github actions with each release however you can also build the PDF or HTML files manually.

Install playwright (which is needed to compile the markdown)
```bash
npm i -g playwright-chromium
```

Run the export command from the root folder of the repository.

```bash
slidev export slides.md
```

This should produce a PDF file called ```slides-export.pdf``` in the root folder of the repository.

