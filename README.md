# Overview

This repo contains my personal website, built using `Franklin.jl`. Some aspects to note

* I have customised the `.github/workflows/Deploy.yml` file. The default (as provided by `Franklin` used an approach which essentially build the site, pushing the contents of the results `_size/` directory (contains static site) to a dedicated `gh-pages` branch, which was then deployed via GitHub pages. The newer way to do this is to used GitHub actions to directly build and deploy the site, and this is what I have done. I essentially modified the Jekyll example [here](https://github.com/actions/starter-workflows/blob/63bb49fa36a7497ddf10213d052f6ba9c8eee853/pages/jekyll.yml), which was mentioned in the `Franklin.jl` [docs](https://franklinjl.org/workflow/deploy/#migrating_to_the_new_github_pages_infrastructure).
