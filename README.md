# building-custom-fabric-ai-patterns
Documenting the process of creating custom patterns for `fabric-ai`
# Purpose
Outline the process of constructing your own pattern for use with `fabric-ai`

# Prerequisites
- `fabric-ai` is installed ([repository here](https://github.com/danielmiessler/fabric?tab=readme-ov-file#just-use-the-patterns))
- A model is configured
- Default patterns are installed / configured
##### Optional:
Since we are dealing with markdown files, you can use `mcat` ([repository here](https://github.com/Skardyy/mcat)) instead of `cat` to view rendered markdown. To install with `Homebrew`:
```
brew install mcat
```

# Setup

##### Understand how the `create_pattern` pattern works:
In Terminal:
```
mcat ~/.config/fabric/patterns/create_pattern/system.md
```
OR

In Finder:
Navigate to `~/.config/fabric/patterns/create_pattern/system.md` and read the document.

#### Provide input for the pattern:
Directly into the command:
```
fabric-ai -p create_pattern 'read text and scramble only the letters between the first and last letters of each word'
```
OR
```
echo 'read text and scramble only the letters between the first and last letters of each word' | fabric-ai -p create_pattern
```

Using a `.txt` file:
```
fabric-ai -p create_pattern < INPUT.txt
```
OR
```
cat INPUT.txt | fabric-ai -p create_pattern
```

#### Work with the output:
Read what the model came up with, and decide if it's how you like it. If it's not how you like it, regenerate.
For a more direct / one-liner, consider appending the output onto another file for editing, if regenerating is too extreme:
```
fabric-ai -p create_pattern 'read text and scramble only the letters between the first and last letters of each word' > OUTPUT.md && vim OUTPUT.md
```
Now the output is a markdown file, which we'll need anyways for the final product.

#### Configure the pattern for `fabric-ai`:
Custom patterns are configured in this structure:
`~/fabric/<custom_patterns_folder>/<pattern_name>/system.md` (`system.md` contains the prompt)
Create a folder to house all current / future custom-made patterns:
```
mkdir -p ~/.config/fabric/custom_patterns
```
- Custom patterns are not overridden when updating the default patterns with `fabric-ai -U`
- The name of the directory can be whatever you want. Create a folder for the specific pattern:
```
mkdir -p ~/.config/fabric/custom_patterns/scramble_letters
```
If you already have the prompt in a markdown file, move it to the `scramble_letters` folder. Make sure to rename it `system.md`
If not, then create a new markdown file with the output and store it in the folder. Here you can copy the output directly and:
```
pbpaste > ~/.config/fabric/custom_patterns/scramble_letters/system.md
```

### Setup is complete
You pattern is now ready to use just like any other pattern. I have attached the corresponding files for the example used throughout this tutorial.
