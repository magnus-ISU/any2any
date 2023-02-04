# any2any
any2any - generate and convert files from any format to any format

## Motivation

How do you convert a markdown file into a pdf?

```
pandoc file.md -o file.pdf
```

How do you convert an image into a pdf?

```
magick file.png file.pdf
```

How do you convert a pdf into text?

```
pdftotext file.pdf file.txt
```

How should all of these work?

```
2 file.anything to file.anything
```

Additionally, this can create file links, like so:

```
2 link_name to real_file
```

as English is a better language to remember how to do this than another random command.

It is unreasonable to expect everyone to know all the commands to do all these; however, there is no reason that you should have to know whether `ffmpeg` requires `-i` or `-o` and in what order. Now, you don't have to.

## How does this work?

This script works by checking a defined list of possible transformations. This has 3 limitations.

1. If multiple ways to convert one file type into another exist, extra effort is required to support both. As most of the time you just want to be able to do *any* kind of transformation, and don't care about the minutia of how it happens.
2. This script cannot easily check if you have the dependencies installed to run a command. But this is not a deal-breaker.
3. Someone has to manually go through and define every way to transform one file into another.

Here, (3) is the greatest threat to this program being useful. Thus, it is self-updating; whenever you encounter a file type it does not handle yet, it will prompt you to explain how to convert that and locally save the method. This on its own is not interesting.

It will also automatically create a github pull request, so that anyone else using the script will *also* get your improvements. Over time, this should mean that all interesting filetypes are convertible.
