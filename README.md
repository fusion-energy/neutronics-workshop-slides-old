Presentation slides for the [neutronics-workshop](https://github.com/fusion-energy/neutronics-workshop)

# View the sides.

The slides are automatically published html format and available here [here](https://fusion-energy.github.io/neutronics-workshop-slides/1).
Every time the main branch of the repository is updated the slides are automatically created and uploaded to the html to the GitHub pages website

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

This is automatically run by Github actions with push to main however you can also build the PDF or HTML files manually.

Install playwright (which is needed to compile the markdown)
```bash
npm i -g playwright-chromium
```

Run the export command from the root folder of the repository.

```bash
slidev export slides.md
```

This should produce a PDF file called ```slides-export.pdf``` in the root folder of the repository.

