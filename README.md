# Create Vite app testing a quick script for better prompt engineering

`npm create vite@latest`

Don't copy and paste code files, ask Claude for a "Can you give me a copy and pastable windows vs code powershell command that takes all the folders and files in my react file src folder and puts them into one .txt"...
Use: Programming, Artifacts, Projects and API
For example:

"Can you give me a copy and pastable windows vs code powershell command that takes all the folders and files in my react file src folder and puts them into one .txt each document can be separated with #### followed by the name and dir of the file"

Returns this:

Get-ChildItem -Path ".\src" -Recurse -File | ForEach-Object { Add-Content -Path "combined_src_files.txt" -Value "#### $($_.FullName.Substring((Get-Location).Path.Length + 5))"; Add-Content -Path "combined_src_files.txt" -Value (Get-Content -Path $_.FullName -Raw); Add-Content -Path "combined_src_files.txt" -Value "nn" }; Write-Host "All files have been combined into combined_src_files.txt"

tip: you can attach something like "FOR ANY CODE FILES MODIFIED ALWAYS GIVE ME THE FULL CODE BACK THANKS" to it as well directly in the powershell command. So you don't need to fuss with Projects, or repeating yourself, painfully starting new conversations etc. Just paste in the command and drag that file into the chat. Much more efficient than other ways.

And it worked, the .txt file is 3000 lines. Where before those were seperated into about 200 lines each.

You don't need a special library, to download anything from github, you can do it with a single powershell command.

https://www.reddit.com/r/ClaudeAI/comments/1ekkkwj/dont_copy_and_paste_code_files_ask_claude_for_a/

```
find ./src -type f | while read file; do
    echo "#### $file"
    cat "$file"
    echo -e "\n\n"
done > src_contents.txt
```

# I don't even want to spend minutes configuring powershell so this does the same thing

# I thought this was an interesting comment for how to do it better

This is smart method what OP showed us. However, it's about 20 years behind the cursor, lol. The new composer is outstanding. I use now custom claude made .cursorrules for each project. Apart from stating critical rules and principles to follow, I also point to .md files that I keep in ./dev, also created by claude, where I have detailed project structure tree, app features, git-branching strategy with already created names and general tasks, file to place new commit messages, changelog, readme and some other stuff. If Claude is well guided like this (by Claude, lol) it can do really complex stuff without getting lost. I try to improve all that files every few hours, learning from mistakes we make. This is so much fun... Poor OP :(

...

Yup exactly. I do the same with .cursorrules. I'll have to implement the way your doing your project structure tree and what not, I like.

Trying to get used to composer but I'm so used to the sidechat

...

Most likely there is a tool for doing that, but instead of searching for it I just quickly wrote a script for that. I did not use side chat even once since I started with composer. To save on fast uses I have constantly opened claude on the second screen. I create a project where I generate and keep all these files I mentioned before. I set different system prompt for the project on claude chat and I use it as self developing knowledge base and guidance. I make Claude on the right write prompts for Claude on the left. Magic 🪄. Every single day I improve my strategy more and more. I guess after I finish my current project I will have to work with both of them strictly on this strategy to get in to next level. Oh, and testing. That's also something I keep always up to date.
