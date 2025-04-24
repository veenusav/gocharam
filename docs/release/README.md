**Context:** intelliGraph
**By:** [N E T R A S E M I](https://netrasemi.com)
# Developer's Notes
This is a markdown file. In VS Code, you can right click on this file to select `Open Preview` to see a formatted document. 
## Table of Contents
1. [Introduction](#introduction)
1. [Project Overview](#project-overview)
1. [Setup Instructions](#setup-instructions)
1. [Configuration guidelines](#configuration-guidelines)
1. [Development Guidelines](#development-guidelines)
1. [Future Improvements](#future-improvements)
1. [References](#references)
1. [Major Revisions](#revisions)

## Introduction
A browser based application to author program through data flow. This is mainly used for AI inference computing where each frame has been computed with different AI operators. 

## Project Overview
Has been done using client only technologies for web. 
* [Js - Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) - 
While it is most well-known as the scripting language for Web pages, many non-browser environments also use it. So, this project can use it for server side too (using node js. aka _back-end_). Started by Chromium, all modern browsers interpret Js in a faster way. So, gives a smooth web application experience(aka _front-end_). 
* [React - UI library (generic)](https://react.dev/) - It gives freedom to write UI 'components' by mixing Js with HTML (JSX files). This open library was by _Meta_. Heavily optimized used for Meta's products, like _Instagram, Facebook_, which is widely used on the internet.
* [ReactFlow - UI library (graph display)](tps://reactflow.dev/) -
A customizable React component for building node-based editors and interactive diagrams. 

The following are major technologies used for development.
* [NodeJs - For Js on desktop](https://nodejs.org) - _Node.js_ is a runtime environment for executing JavaScript code outside browser. This is popular among server side programmers for developing the back-end. Now we are not having server-side component and using this to execute its package npm. see next. 
* [npm - build tool](https://www.npmjs.com/) - Node Package Manager is a package manager used to manage dependencies and packages within Node.js projects. 
* [Vite - webpage build tool](https://vite.dev/) - A fron-end build tool. While we create our program in JSX, this kind of tools are necessary to properly build html, Js files. It provides two modes: _developer and production_. In dev mode, it gives automatic updates when the programmer edits the Jsx files. Production is optimized version for hosting. This French word pronouced like 'veet'.


## Setup Instructions
When you want to setup a dev environment for the first time, 
* Try `node` in the os shell. If not working, install [NodeJs](https://nodejs.org) from their website.
If you 
* Go the folder with our code (outside src folder).
* Execute `npm install`. It will use package.json file and setup everything for the development. 

This is a web application host and test kind of programmer environment. so, after this setup, you may check Development guidelines section for further usage.
## Configuration guidelines
This version does not use a webserver. All code will be run at the browser environment.
Other than code, the following files are relevant for an explanation.

| # | File | Details |
|---|---|---|
| 1   | functionlibs.json | This lists all the function template libraries used in the system. Suggest to use `stdfunctions01.json` as default. You may add domain specific other json files for those function libraries. For example `survillance.json` for *home survilliance functions*. To showcase the file-format, we added `xdomain.json` and `ydomain.json`.  |
| 2   | stdfunctions01.json | This is meant to keep all standard functions. The filename `stdfunctions01` can be changed by changing its name in `functionlibs.json` |
| 3   | functions_doc.json | This is a place to document all the attribute titles. Also shown some special formats like composite object with attribute linkages. This is only provided for documentation. Not used by the program. Please add all the attribute formats into this for a comprehensive reference for those who make new function template |
| 4   | functions.csv | This is used to list the left side panel of the program which is called library. All the functions listed in the json files (referred through functionlibs.json) are listed here for library display with icons and description. The unique function id is used to link between the jsons and csv. Kindly note that listing here in this file will not show on library. for that we need to refer the function under one or more *collection*   |
| 5   | collections.csv | These are the primary list shown in library. Each entry in the collections referred as a *collection*. For example *cv* or *computer vision*. In cv collection there will be functions tagged to that. Another collection can be *AI*. |
| 6   | coll_cv.csv | These csvs are the secondary list shown in library under a collection. Each entry in these CSVs refer a *function id* in `functions.csv`. All these collection related CSVs should start with `coll_`. `coll_cv` is an example of `coll_xxx` type of csv. Here, it is collection meant for **cv** (*computer vision*).  |

* Through `functionlibs.json` the system lists all the function templates which can be placed by the user from library as well as canvas context menu.

* One of more collections can list same function. for example computer vision function can be in the AI collection.

* `ctrl .` is the hotkey to load functionlibs.json dynamically.

## Development Guidelines
##### Todo: Outline the coding standards, best practices, and tools used.
* Temporary files: There is a file called `.gitignore`, it gives certain pointers for discarding temporary files. For example, npm install will create folders such as `node_modules`. These temp things will not be considered by git. Also, when you take back, do not take these.
* `npm run xyz` can be done for running certain command `xyz`. To know available commands, see scripts section of package.json. 
* `npm run dev` - to run the development server. Then you can open the web page on a browser from localhost. Instructions will be available on os shell. normally it appers at http://localhost:5173/ . Since this is _dev_ mode, while running the application, your edits in the source jsx files will be reflected realtime. This is a cool feature for the programmer. `:D`  
* `npm run build` - to prepare a producation quality output. After executing the complete webpage will be created in `dist` directory. To run and check you can call `npm run preview`. 
* `npm run preview` - to host a local server to check production quality web page. This will only work after `build`. Normally it appears at http://localhost:4173/.  Also, as this is not meant for realtime coding like `npm run dev`, your jsx editing will not be updated realtime.  


## Future Improvements 
*Section for potential improvements or features to be added.*

| # | Brief | Details |status |
|---|---|---|----|
| 1   | Local file system store | store/retrieve data to hard disk files. `May be Webserver too` | done|
| 2   | Attributes | Rich attibute data entery UI has to be done| done |
| 3   | function-type procesing in editor | When a function (that is node) is configured, its core part is its formulation. that is called function-type. This can be configured with js files by the platform providers. This has been prototyped and tested with dynamic JS loading and function invocation. Even function-type specific attributes will be populated for for the graph definition. The attibute's value will be validated using these dynamic function-type Js. `NS`  | done. but need to enrich with types|
| 4 | Exchange format | This is a graph based programming language. Exchange of information can be done through a defined data structure through text format like JSON. There will be defintion part and an instance part. the definition gives bare minimum information of the data flow with functions and flow.(aka nodes and edges). The instane gives all the parameters (known as attributes to nodes) for creating a meaningful processing at the target platform. From the definition, the tool chain could retarget a new instance whenever required. These concepts has to be implemented. And the exchange format should be validated at the UI level. later this can be fed to tensorflow based AI target platform.`NS`| check needed |
| 5   | Library | storing pre-configured functions as library for ready-made use `in progress`| sub graph tbd |
| 6   | Automatic layouting | Functions and flow are the definition of the logic. The diagram can be generated with automated algorithms.| need to do. also horizontal dir|
| 7   | Printing / Documentation | Pagination, Header, Footer|| tbd|

## References
*Section to include any references or resources that are helpful for development.*

1. for powershell, I usually like short prompts. so use the following scrip (Just paste on the PS prompt then enter):

```PS
function prompt {
    "| " + (get-location).Path.Split('\')[-1] + "> "
}
```
2. The icons used are Solar Broken Line Icons Collection from https://www.svgrepo.com/collection/solar-broken-line-icons/. ofcourse, there might be some changes. 
1. Good for theme based color selection - https://colorhunt.co/palette/c14600ff9d23e5d0acfef9e1

## Revisions
*Include all the major changes.*

| Date | Person | Notes |
|---|---|---|
| 2025 Feb 7 | Veenus | Created|
| 2025 Feb 25 | Veenus | Released a browser local saved version with only graphics attibutes|
| 2025 Mar 16 | Veenus | Local disk save graphs, better json format, attribute dlg, port configurations|
| 2025 Apr 08 | Veenus | Undo redo , node selection, composite function json style|
| 2025 Apr 23 | Veenus | Library with dynamic json Function templates instead of hardcoded jsx file, Better Library panel with sub scrollbars for collections  |


**End of File**
