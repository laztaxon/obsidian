used chatgpt to create a script to help me create a new linked note in [[tmux]] [[nvim]] [[obsidian]]
i need a lua script that will work within neovim and tmux to interact with obsidian, the script should do the following:
starts with focus a .md file inside my obsidian vault ~/Documents/cello-main
<script in lua>
1. check that we are in a tmux session
2. request note name
3. create new note in obsidian vault with given name
4. append the markdown link [[]] to the file i was originally writing in.
5. use tmux to open a bottom pane to the newly created linked markdown file 
</script in lua>

## Output v1:

