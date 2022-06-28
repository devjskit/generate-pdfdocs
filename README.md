## ⚠️ Caution!

Currently, this package is not catching up with docusaurus v2 HTML markup, so command may not find the correct HTML to loop through docs. Please modify the command to find correct HTML markup by yourself.

## 📌 Introduction

This is a PDF generator from document website such as `docusaurus`, `vuepress`, `mkdocs`.

## ⚡ Usage

For [docusaurus v1](https://v1.docusaurus.io/docs/en/installation)

```shell
npx generate-pdfdocs --initialDocURLs="https://v1.docusaurus.io/docs/en/installation" --paginationSelector=".docs-prevnext > a.docs-next" --excludeSelectors=".fixedHeaderContainer,footer.nav-footer,#docsNav,nav.onPageNav,a.edit-page-link,div.docs-prevnext" --cssStyle=".navPusher {padding-top: 0;}" --contentSelector="article"
```

## 🍗 CLI Options

| Option                 | Required | Description                                                                                                                                                                        |
| ---------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--initialDocURLs`     | Yes      | set URL to start generating PDF from.                                                                                                                                              |
| `--contentSelector`    | Yes      | used to find the part of main content                                                                                                                                              |
| `--paginationSelector` | Yes      | CSS Selector used to find next page to be printed for looping.                                                                                                                     |
| `--excludeURLs`        | No       | URLs to be excluded in PDF                                                                                                                                                         |
| `--excludeSelectors`   | No       | exclude selectors from PDF. Separate each selector **with comma and no space**. But you can use space in each selector. ex: `--excludeSelectors=".nav,.next > a"`                  |
| `--cssStyle`           | No       | CSS style to adjust PDF output ex: `--cssStyle="body{padding-top: 0;}"` \*If you're project owner you can use `@media print { }` to edit CSS for PDF.                              |
| `--outputPDFFilename`  | No       | name of the output PDF file. Default is `generate-pdfdocs.pdf`                                                                                                                     |
| `--pdfMargin`          | No       | set margin around PDF file. Separate each margin **with comma and no space**. ex: `--pdfMargin="10,20,30,40"`. This sets margin `top: 10px, right: 20px, bottom: 30px, left: 40px` |
| `--pdfFormat`          | No       | pdf format ex: `--pdfFormat="A3"`. Please check this link for available formats [Puppeteer document](https://pptr.dev/#?product=Puppeteer&version=v5.2.1&show=api-pagepdfoptions)  |
| `--disableTOC`         | No       | Optional toggle to show the table of contents or not                                                                                                                               |
| `--coverTitle`         | No       | Title for the PDF cover.                                                                                                                                                           |
| `--coverImage`         | No       | `<src>` Image for PDF cover (does not support SVG)                                                                                                                                 |
| `--coverSub`           | No       | Subtitle the for PDF cover. Add `<br/>` tags for multiple lines.                                                                                                                   |
| `--headerTemplate`     | No       | HTML template for the print header. Please check this link for details of injecting values [Puppeteer document](https://pptr.dev/#?product=Puppeteer&show=api-pagepdfoptions)      |
| `--footerTemplate`     | No       | HTML template for the print footer. Please check this link for details of injecting values [Puppeteer document](https://pptr.dev/#?product=Puppeteer&show=api-pagepdfoptions)      |
|                        |          |                                                                                                                                                                                    |

## 🎨 Examples and Demo PDF

### Docusaurus v1

<https://docusaurus.io/en/>

`initialDocURLs`: <https://docusaurus.io/docs/en/installation>

`demoPDF`: <https://github.com/kohheepeace/generate-pdfdocs/blob/master/v1-docusaurus.pdf>

`command`:

```shell
npx generate-pdfdocs --initialDocURLs="https://docusaurus.io/docs/en/installation" --paginationSelector=".docs-prevnext > a.docs-next" --excludeSelectors=".fixedHeaderContainer,footer.nav-footer,#docsNav,nav.onPageNav,a.edit-page-link,div.docs-prevnext" --cssStyle=".navPusher {padding-top: 0;}" --pdfMargin="20"
```

### Docusaurus v2 beta

![20210603060438](https://user-images.githubusercontent.com/29557494/120552058-b4299e00-c431-11eb-833e-1ac1338b0a70.gif)

<https://docusaurus.io/>

`initialDocURLs`: <https://docusaurus.io/docs>

`demoPDF`: <https://github.com/kohheepeace/generate-pdfdocs/blob/master/v2-docusaurus.pdf>

`command`:

```shell
npx generate-pdfdocs --initialDocURLs="https://docusaurus.io/docs/" --contentSelector="article" --paginationSelector=".pagination-nav__item--next > a" --excludeSelectors=".margin-vert--xl a" --coverImage="https://docusaurus.io/img/docusaurus.png" --coverTitle="Docusaurus v2"
```

### Vuepress v1

<https://vuepress.vuejs.org/>

`initialDocURLs`:

<https://vuepress.vuejs.org/guide/>

`demoPDF`: <https://github.com/kohheepeace/generate-pdfdocs/blob/master/v1-vuepress.pdf>
`command`:

```shell
npx generate-pdfdocs --initialDocURLs="https://vuepress.vuejs.org/guide/" --contentSelector="main" --paginationSelector=".page-nav .next a" --excludeSelectors="header.navbar,aside.sidebar,footer.page-edit .edit-link,.global-ui,.page-nav" --coverImage="https://vuepress.vuejs.org/hero.png" --coverTitle="VuePress" --coverSub="Vue-powered Static Site Generator"
```

### Vuepress v2 beta

<https://v2.vuepress.vuejs.org/>

`initialDocURLs`:

<https://v2.vuepress.vuejs.org/guide/>

`demoPDF`: <https://github.com/kohheepeace/generate-pdfdocs/blob/master/v2-vuepress.pdf>
`command`:

```shell
npx generate-pdfdocs --initialDocURLs="https://v2.vuepress.vuejs.org/guide/" --contentSelector="main" --paginationSelector=".page-nav .next a" --excludeSelectors="header.navbar,aside.sidebar,footer.page-edit .edit-link,.global-ui,.page-nav" --coverImage="https://v2.vuepress.vuejs.org/images/hero.png" --coverTitle="VuePress" --coverSub="Vue-powered Static Site Generator"
```

### Mkdocs

<https://www.mkdocs.org/>

`initialDocURLs`: <https://www.mkdocs.org/>

`demoPDF`: <https://github.com/kohheepeace/generate-pdfdocs/blob/master/mkdocs.pdf>

`command`:

```shell
npx generate-pdfdocs --initialDocURLs="https://www.mkdocs.org/" --paginationSelector="ul.navbar-nav li.nav-item a[rel~='next']" --excludeSelectors=".navbar.fixed-top,footer,.homepage .container .row .col-md-3,#toc-collapse" --cssStyle=".col-md-9 {flex: 0 0 100%; max-width: 100%;}"
```

### Material for Mkdocs

<https://squidfunk.github.io/mkdocs-material/>

`initialDocURLs`: <https://squidfunk.github.io/mkdocs-material/getting-started/>

`demoPDF`: <https://github.com/kohheepeace/generate-pdfdocs/blob/master/material-for-mkdocs.pdf>
`command`:

```shell
npx generate-pdfdocs --initialDocURLs="https://squidfunk.github.io/mkdocs-material/getting-started/" --paginationSelector="a.md-footer-nav__link--next" --excludeSelectors="header.md-header,.announce,nav.md-tabs,.md-main__inner .md-sidebar--primary,.md-main__inner .md-sidebar--secondary,footer" --cssStyle=".md-content {max-width: 100%!important;}"
```
