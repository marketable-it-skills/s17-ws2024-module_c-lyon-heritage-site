# Introduction

Welcome to Lyon. This vibrant city is known for its historical significance and architectural beauty. In this project, some editors wrote some articles to introduce notable heritage sites in Lyon, France. Each article is written in .html or .txt format, with a front-matter embedded at the beginning of each article for meta information. These files are stored in a folder called "content-pages". Some article files may be stored in sub-folders, or nested subfolders.

There is one "images" folder under "content-pages" folder. All image path mentioned in these articles and all relative to this images folder. That means no images folder inside nested sub-folders. It means when referring to any image names in articles inside sub-folders, these images are all refer to this images folder under the "content-pages" folder.

You are asked to create a website to host these articles. Each article becomes "page", that we refer in the following document. In order to keep the current article writing workflow, we will keep the existing structure of "content-pages" folder unchanged.

In this module, we create a site that lists and loads these files and sub-folders. The site reads these static files from a "content-pages" folder and display the content as web pages. The naming convention for the pages is YYYY-MM-DD-title.txt, or YYYY-MM-DD-title.html.

The web site is reachable at <http://wsXX.worldskills.org/XX_module_C/> XX is your seat number.

# Description of project and tasks

There is no need to use database in this project. The content is stored in the "content-pages" folder, or subfolders inside it. Anyone can access the home page and the heritage sites page. When accessing the home page, there should be a list of all pages and sub-folders.

## URL Routes and mapping

There are URL routes definition for listing content folder, pages, and querying tags. The URL to each page or sub-folder is defined as following. XX is your seat number.

_/XX_module_c/_ shows the index listing.

_/XX_module_c/heritages/2024-09-01-example-page_ shows the page for 2024-09-01-example-page.html or 2024-09-01-example-page.txt

_/XX_module_c/heritages/sub-folder-name_ lists the pages and folders of the specific sub-folder.

_/XX_module_c/heritages/sub-folder-name/2024-09-10-welcome-to-lyon_ shows the page of 2024-09-10welcome-to-lyon.html or 2024-09-10-welcome-to-lyon.txt in the "sub-folder-name" folder.

_/XX_module_c/heritages/sub-folder-1/sub-folder-2/2024-09-10-welcome-to-lyon_ shows the page of 2024-09-10welcome-to-lyon.html or 2024-09-10-welcome-to-lyon.txt in the "sub-folder-1/sub-folder-2/" folder.

The URL for tags querying is defined as following.

/XX_module_c/tags/tag-name-here shows a page that lists all the pages that contains given tag "tag-namehere"

Note: The paths above are relative to _<http://wsXX.worldskills.org>_

## Filename convention

The filename contains the date, and the title in slug form. It is "YYYY-MM-DD-title-in-lower-case-withhyphens.html", or ".txt".

The first part of the filename is in YYYY-MM-DD format, YYYY for the year in 4 digits, MM for months in 2 digits, and DD for day in 2 digits.

The second part of the filename is the title of the file, in slug form. That is a lower case of the title with all spaces replaced by hyphens.

Here are some sample filenames:

- 2024-09-01-example-page.html
- 2024-10-20-greatest-lyon-heritage-site.html
- 2025-01-01-a-post-for-future-posting.txt

# Listing content

When listing the content, the list shows the title, and the summary. Clicking either on the title or summary will link to that single content.

The list should not list future pages, which the date is in the future, after today.

The list also should not list pages in draft state, which the draft is "true" defined in the front-matter of the file.

The list should also hide pages without any dates defined. That is when the first 11 characters is not in the format of "YYYY-MM-DD-".

Aside from the pages, the list also lists and links to sub-folders. When click on the sub-folder name, the web lists the content within the sub-folder. That is the pages and sub-folders inside that sub-folder.

### Ordering of content listing

The list lists sub-folders first, then it lists the content pages. The sub-folders are listed in alphabetical order. The content pages are listed in reversed alphabetical order. That will result in having the latest pages on the top and oldest pages at the bottom.

# Accessing content pages

Each file in the content-pages folder contains one heritage content. It includes a path to the cover image, tags, summary and may be the title.

In each file, there are two parts in each file content: Front-matter, and the main content.

The front-matter is optional. if there is front-matter, it will be marked with "---" at both beginning and ending of the front-matter section.

Here is an example content in .html extension, with front-matter embedded.

\---

title: This is an Example Page tags: example, test cover: example-cover.jpeg summary: This is a sample summary.

\---

&lt;h1&gt;Example Page&lt;/h1&gt;

&lt;p&gt;Here is the rest of the content.&lt;/p&gt;

&lt;p&gt;And some other paragraph.&lt;/p&gt;

&lt;img src="hello-world.jpg" alt="Sample photo"&gt;

&lt;footer&gt;That is all&lt;/footer&gt;

Here is an example content in .txt extension format.

\--- title: This is another sample page tags: example, test, plain-text cover: another-cover.jpeg summary: This is a sample page in txt format. ---

This is sample main content.

Each line of content is turned into &lt;p&gt;&lt;/p&gt; paragraph.

sample-image.jpeg

The image path / image name with individual line are turned into &lt;img&gt; tag.

This is footer paragraph.

The files in the "content-pages" folder can be nested into sub-folders.

### Front-matter

There may be front-matter in the beginning of the content file.

There may be different key-value pairs defined in the front-matter section. They are:

- title (optional)
- tags (optional): separated by comma, or comma with spaces
- draft (optional): true, or other values. Any values other than "true" is considered as false.
- summary (optional): One line only. To be used when listing the pages.

# Rendering a heritage site web page

In the rendered page, there are following sections:

- Cover image,
- Title,
- aside information,
- main content

### Cover Image

The path to the cover image of each content page is defined in the front-matter by default.

If the cover image is not defined in the front-matter, the cover image will be the same file name stored in the images folder. In this project, we don't need to consider the missing of this cover image.

### Cover image styling

There is a subtle spotlight effect on the cover image.

A radial gradient of mask is applied to the cover image. The mask is circle with center point following the mouse pointer, gradient from black to rgba(255,255,255,0) 300px.

Please refer to the cover-image-styling.mp4 in the media files.

### On the extraction of title

There is a Title section after the cover image. The content of the title is decided according to the following criteria.

The title should be extracted from the following, in order.

1. When there is "title" defined in the front-matter, the content of Title section uses the value of this frontmatter
2. When there is no "title" defined in the front-matter, the content of Title section use the text content of first &lt;h1&gt;&lt;/h1&gt; (Simple text content, the h1 will not be rich HTML)
3. When no any "title" in front-matter nor no h1 tag in the content, the content of Title section uses the capitalization of the file name, without extension and the YYYY-MM-DD date content. Also, all the hyphen slugs (-) are removed and replaced into spaces.

**Styling of the title section**

Please use the common-ligatures typography setting on the title styling.

### Aside information

There are following information in the aside information area.

date, tags, draft (If the draft is true)

The meta information on the side is sticked to the top when scrolling down.

### Rendering main content

The main content should be dynamic loaded from the files.

Here are some file loading strategies.

If the file extension is .html, the main content and any HTML tags are rendered as is. No need to parse or process (Except the image path). They are just rendered as the HTML.

If the file extension is .txt, there will only be two kind of content. Lines of text and individual line containing image path. Each line of text is turned into HTML paragraphs.

Individual line of image path is turned into image tag. These are lines without any spaces and with image extensions at the end.

For both .html and .txt, the image paths should be replaced to fit final image paths that work on server.

The photos in the content area have full-width to the main content container. The photos in the main content area can be enlarged when user clicks on the photos. Clicking the enlarged photo will close the enlarged photo and revert to the main content. Scrolling during photo enlarged will also close the enlarged photo and revert to the main content.

The first letter of the first paragraph has drop cap for 3 lines.

# Tags

Content pages can be filtered by tags. The URL for tags querying is defined as following.

<http://wsXX.worldskills.org/XX_module_c/tags/tag-name-here> shows a page that lists all the pages that contains given tag "tag-name-here".

### Searching

The web page should be able to search for pages. Please provide a search input and user should be able to search for title or content. Given a search query, the web page should list pages that either the title or the content contains the query string.

It should be able to use "/" to define multiple keywords for searching. And the page list the page with title or content that contains either keyword, in OR logic.

# Instructions to the Competitor

You may put your project in a sub-folder or different port. Please redirect to your destination from the path wsXX.worldskills.org/XX_module_c/

For example, _/XX_module_c/heritages/sub-folder-name_ may be _/XX_module_c/public/heritages/sub-folder-name_ or _/XX_module_c/index.php/heritages/sub-folder-name_ or _:3000/XX_module_c/heritages/sub-folder-name._

Note if you are using NodeJS, please be aware of the node_modules files for Windows (on workstation) and Linux (on server) is different. Using a wrong node_modules folder may result in unexpected error.

You may provide a README file for executing guide if necessary.

Please consider better accessibility. Full page scan will be performed by using the aXe accessibility dev tool.

Please define social sharing meta tags for each single heritage page for sharing friendly purpose.

Please define the .gitignore file to skip node_modules folder and other temporary folder or built folder.

This project will be assessed by using Google Chrome web browser.

## Marking Summary

|     | **Sub-Criteria**  | **Marks** |
| --- | ----------------- | --------- |
| 1   | Files and Listing | 7.0       |
| 2   | Search and Tags   | 2.0       |
| 3   | Loading files     | 5.5       |
| 4   | Layout            | 6.75      |
