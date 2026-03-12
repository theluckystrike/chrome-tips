---
layout: default
title: Chrome Print to PDF Command Line
description: Learn how to use Chrome print to PDF from command line for automated web-to-PDF conversion. Complete guide with examples and practical use cases.
date: '2026-03-12'
last_modified_at: '2026-03-12'
permalink: chrome-print-to-pdf-command-line
categories:
- browser-tips
- pdf
- automation
- command-line
tags:
- chrome
- print-to-pdf
- command-line
- automation
- headless
author: theluckystrike
---

# Chrome Print to PDF Command Line

If you need to convert web pages to PDF files automatically, Chrome offers powerful command-line options that can handle this without opening the browser window. The chrome print to PDF command line feature lets you script web-to-PDF conversions, making it useful for developers, content managers, and anyone who regularly needs to save web pages as formatted documents.

## Why Use Command Line for PDF Generation

Manual PDF creation through Chrome's print dialog works fine for occasional use, but becomes time-consuming when you need to convert multiple pages or run the process on a schedule. Command-line options let you automate this completely. You can set up scripts that run overnight, process batches of URLs, or integrate PDF generation into larger workflows.

Many professionals find this approach valuable. Marketers might need to archive landing pages for compliance. Researchers may want to save online articles for offline reading. Developers often need to generate PDFs of web-based reports automatically. The command-line approach handles all of these scenarios efficiently.

## Basic Chrome Print to PDF Command

The foundation of chrome print to PDF from command line is the `--print-to-pdf` flag. This option runs Chrome in headless mode, meaning it operates without a visible window, and outputs a PDF directly.

The simplest version looks like this:

```
chrome --headless --print-to-pdf=output.pdf https://example.com
```

On macOS, you would use the application path:

```
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --headless --print-to-pdf=output.pdf https://example.com
```

On Linux, the command typically is:

```
google-chrome --headless --print-to-pdf=output.pdf https://example.com
```

Windows users can run:

```
"C:\Program Files\Google\Chrome\Application\chrome.exe" --headless --print-to-pdf=output.pdf https://example.com
```

## Customizing Output Settings

The basic command works, but you can add several options to control the PDF output. The `--print-to-pdf` flag accepts additional parameters that modify the result.

To disable headers and footers that Chrome adds by default, use:

```
--print-to-pdf=no-header-footer output.pdf https://example.com
```

This removes the URL, date, and page numbers that normally appear on printed pages.

For landscape orientation:

```
--print-to-pdf=output.pdf --landscape https://example.com
```

You can also set a specific paper size:

```
--print-to-pdf=output.pdf --paper-width=8.5 --paper-height=11 https://example.com
```

These measurements are in inches by default.

## Handling Multiple Pages

When a web page spans multiple printed pages, Chrome automatically handles the pagination. However, you might want more control over how content breaks across pages. The `--prefer-css-page-size` option tells Chrome to use the CSS page settings defined in the webpage itself rather than applying defaults:

```
--print-to-pdf=output.pdf --prefer-css-page-size https://example.com
```

This works well for pages designed with print stylesheets.

## Batch Processing Multiple URLs

For converting multiple web pages at once, you can create a simple shell script. On macOS or Linux:

```bash
#!/bin/bash
for url in "$@"; do
    filename=$(echo "$url" | sed 's/[^a-zA-Z0-9]/_/g').pdf
    /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --headless --print-to-pdf="$filename" "$url"
done
```

Save this as `batch-pdf.sh` and run:

```
./batch-pdf.sh https://example.com/page1 https://example.com/page2 https://example.com/page3
```

Each URL will be converted to a separate PDF file.

## Practical Automation Examples

One common use case involves generating daily reports. If you have a web-based dashboard that updates each day, you can create a cron job that runs each morning and saves the current state as a PDF. This provides an automatic backup and makes it easy to review past data.

Another practical application involves archiving content. Some websites change frequently or eventually disappear. Running a command-line script weekly to save important pages ensures you always have a local copy. This is especially valuable for reference pages, documentation, or content that serves as a business resource.

For developers, integrating Chrome PDF generation into build processes helps maintain updated documentation. Many projects host their docs as web pages but need PDF versions for offline distribution. A simple script can regenerate these PDFs whenever the documentation updates.

## Troubleshooting Common Issues

Sometimes the PDF output does not match expectations. Several common problems have straightforward solutions.

If the PDF appears empty or cut off, the page may be using heavy JavaScript to render content. Adding a delay can help:

```
--virtual-time-budget=10000
```

This gives the page extra time to load dynamic content before printing.

When fonts look wrong in the output, the page may be using web fonts that do not render in headless mode. You cannot always fix this, but checking the output and adjusting your workflow accordingly helps.

For pages that require login, command-line Chrome cannot handle authentication directly. You would need to first obtain a cookie or session data and pass it to Chrome, which adds complexity beyond basic PDF generation.

## Browser Extensions and Additional Tools

While the command-line approach works well for technical users, browser extensions offer simpler alternatives for casual use. Tab Suspender Pro, for example, helps manage open tabs efficiently, though it focuses on memory management rather than PDF generation. Extensions that specifically handle PDF creation often provide more visual control over the output.

For organizations needing enterprise-level PDF generation at scale, consider combining Chrome's command-line capabilities with scheduling tools, monitoring systems, or content management integrations. The flexibility of command-line access makes it possible to build sophisticated automation pipelines.

## Getting Started

To begin using chrome print to PDF from command line, start with the basic command and a single URL. Verify that the output matches your expectations, then gradually add options like header removal or landscape orientation. Once comfortable with single-page generation, move on to batch scripts that handle multiple URLs.

The learning curve is gentle, and the payoff comes quickly. Even a simple script that saves three or four important pages automatically each week can save significant time over months of manual work.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
