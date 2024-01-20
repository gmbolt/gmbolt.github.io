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
ignore = ["node_modules/", "franklin.md"]

# Keep paths - Franklin.jl will leave these files "exactly as is"
keep_path = ["google6d0f2989942ef341.html", "googleb18be41324b9dc6b.html", "data_on_lake_2022/", "isba_2022/", "itam_2023/", "data_local/"]

# RSS (the website_{title, descr, url} must be defined to get RSS)
generate_rss = true
website_title = "George Bolt"
website_descr = "Personal website."
website_url   = "https://gmbolt.github.io/"
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
            <p><a href="!#3">Learn more...</a></p>
        </div>
    </div>
    ~~~
}
<!-- Figure - args: 1=path to file; 2=caption; 3 = width -->
\newcommand{\figenv}[3]{    
    ~~~
    <figure style="text-align:center;">
    <img src="!#1" style="padding:0;#3" alt="#1"/>
    <figcaption style="margin-left: auto; margin-right: auto;">#2</figcaption>
    </figure>
    ~~~
}