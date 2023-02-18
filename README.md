Presentation slides for the [neutronics-workshop](https://github.com/fusion-energy/neutronics-workshop)

# View the sides.

The slides are automatically published html format and available [here](https://fusion-energy.github.io/neutronics-workshop-slides/1).

Every time the main branch of the repository is updated the slides are automatically rebuilt and uploaded as html to the GitHub pages website

# Develop the slides

To contribute or edit these slides you will need a few packages installing.

## Install slidev

The slides are built using [sli.dev](https://sli.dev/) which can be installed with a npm command.

```bash
npm i -g @slidev/cli
```

clone the repository
git clone https://github.com/fusion-energy/neutronics-workshop-slides.git

navigate to the root folder of the repository

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

You can also build the PDF files manually if required.

Install playwright (which is needed to compile the markdown)
```bash
npm i -g playwright-chromium
```

Run the export command from the root folder of the repository.

```bash
slidev export slides.md --output slides.pdf
```

This should produce a PDF file called ```slides.pdf``` in the root folder of the repository.

## Exporting the slides to HTML

A HTML file is automatically built by Github actions whenever a push to main is made, however you can also build the HTML files manually.
Carry out the same steps as the [GitHub action](https://github.com/fusion-energy/neutronics-workshop-slides/blob/main/.github/workflows/deploy.yml) to build local HTML files

