<!--
Add here global page variables to use throughout your website.
-->
+++
author = "George Bolt"
mintoclevel = 2

# Add here files or directories that should be ignored by Franklin, otherwise
# these files might be copied and, if markdown, processed by Franklin which
# you might not want. Indicate directories by ending the name with a `/`.
# Base files such as LICENSE.md and README.md are ignored by default.
ignore = ["node_modules/"]

# RSS (the website_{title, descr, url} must be defined to get RSS)
generate_rss = true
website_title = "George Bolt"
website_descr = "Personal website."
website_url   = "https://tlienart.github.io/FranklinTemplates.jl/"
+++

<!--
Add here global latex commands to use throughout your pages.
-->
\newcommand{\R}{\mathbb R}
\newcommand{\scal}[1]{\langle #1 \rangle}
\newcommand{\card}[4]{
    ~~~
    <div class="card" onclick="location.href='!#3'" style="cursor: pointer;">
        <img src="!#4" style="padding-left:0;width:100%;height:300px;object-fit:cover;border-radius: 0px 0px 0 0">
        <div class="container">
            <h3 style="padding-bottom: 0px;margin-top: 16px;margin-bottom: 0px; font-size: 25px;"><b>!#1</b></h3>
            <p>!#2</p>
            <p><a href="!#3" class="btn btn--primary">Learn more</a></p>
        </div>
    </div>
    ~~~
}