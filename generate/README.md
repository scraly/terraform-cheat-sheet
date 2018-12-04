# Generate

## Pre-requisits

`$ npm i yargs --save`

## 1. Markdown to AsciiDoc

`$ pandoc -s --columns=80 --atx-headers -t asciidoc -o out.adoc README.md`

##2. Asciidoc to PDF

`$ ./bin/asciidoctorjs-pdf terraform-cheat-sheet.adoc --template-require ../examples/cheat-sheet/template/template.js`
