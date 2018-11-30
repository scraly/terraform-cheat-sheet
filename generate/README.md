# Generate

## 1. Markdown to AsciiDoc

`$ pandoc -s --columns=80 --atx-headers -t asciidoc -o out.adoc README.md`

##2.

`$ ./bin/asciidoctorjs-pdf /home/scraly/git/src/github.com/scraly/terraform-cheat-sheet/out.adoc --template-require ../examples/cheat-sheet/redhat/template.js`
