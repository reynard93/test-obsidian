prettier/eslint not ls but can use null-ls to connect them

vim.keymap.set("n", "<C-g>", live_grep_in_directory, {})
vim.keymap.set("n", "<leader>tgs", stash_filter, {}
vim.keymap.set("n", "<localleader>vr", function() M.get_component_references() end)
	local keymap is ","

vim.keymap.set("n", "<C-f>", live_grep, {})
["<C-y>"] = CopyTextFromPreview,
["<C-h>"] = OpenInFileBrowser,


vim.keymap.set("n", "<C-c>", current_buffer_fuzzy_find, {})
vim.keymap.set("n", "<C-j>", git_files, {})
vim.keymap.set("n", "<C-m>", telescope.extensions.file_browser.file_browser, { silent = true, noremap = true })

vim.keymap.set("n", "<leader>tgc", git_commits, {})
	["<C-y>"] = CopyCommitHash,
	["<C-o>"] = SeeCommitChangesInDiffview,
	["<C-d><C-f>"] = CompareWithCurrentBranchInDiffview,

vim.keymap.set("n", "<leader>tgb", git_branches, {})
["<Enter>"] = CheckoutAndRestore,

vim.keymap.set("n", "<leader>tf", grep_string, {})
vim.keymap.set("v", "<leader>tf", grep_string_visual, {})

vim.keymap.set("n", "<C-h>", OpenFileInFileBrowser)
[","] = fb_actions.goto_parent_dir,
["<C-e>"] = fb_actions.create,
["<C-k>"] = fb_actions.remove,
["<C-r>"] = function(bufnr)fb_actions.rename(bufnr)end,
["<C-x>"] = fb_actions.move, (after using tab or s-tab to select), or <c-s> to select all
// can look at https://github.com/nvim-telescope/telescope-file-browser.nvim
<C-h> to toggle hidden
<C-f> toggle btwn file and folder browser
-- navigate telescope results thru c-n and c-p

[c-z] is replaced to open terminal

bqf maybe ii dont need yet, dk how use i disabled
conjure, really nice plugin for interactive code eval, TODO: set it up for rust
<C-n/p> to surf fwd and bwd buffers, 
H to write

TOGGLE
<leader>gfh git file history
<leader>gh git history
<leader>gc/go git changes
key_bindings = {
disable_defaults = true, -- Disable the default key bindings
-- The `view` bindings are active in the diff buffers, only when the current
-- tabpage is a Diffview.
view = {
["<C-n>"] = cb("select_next_entry"), -- Open the diff for the next file

["<C-p>"] = cb("select_prev_entry"), -- Open the diff for the previous file

["<CR>"] = cb("goto_file_edit"), -- Open the file in a new split in previous tabpage

["<C-w><C-f>"] = cb("goto_file_split"), -- Open the file in a new split

["<C-w>gf"] = cb("goto_file_tab"), -- Open the file in a new tabpage

["<leader>e"] = cb("focus_files"), -- Bring focus to the files panel

["<leader>b"] = cb("toggle_files"), -- Toggle the files panel.
},

file_panel = {

["j"] = cb("next_entry"), -- Bring the cursor to the next file entry

["<down>"] = cb("next_entry"),

["k"] = cb("prev_entry"), -- Bring the cursor to the previous file entry.

["<up>"] = cb("prev_entry"),

["o"] = cb("select_entry"),

["<2-LeftMouse>"] = cb("select_entry"),

["-"] = cb("toggle_stage_entry"), -- Stage / unstage the selected entry.

["S"] = cb("stage_all"), -- Stage all entries.

["U"] = cb("unstage_all"), -- Unstage all entries.

["X"] = cb("restore_entry"), -- Restore entry to the state on the left side.

["R"] = cb("refresh_files"), -- Update stats and entries in the file list.

["<C-u>"] = actions.scroll_view(-20),

["<C-d>"] = actions.scroll_view(20),

["<C-n>"] = cb("select_next_entry"),

["<C-p>"] = cb("select_prev_entry"),

["gf"] = cb("goto_file"),

["<cr>"] = cb("goto_file_tab"),

["i"] = cb("listing_style"), -- Toggle between 'list' and 'tree' views

["f"] = cb("toggle_flatten_dirs"), -- Flatten empty subdirectories in tree listing style.

["<leader>e"] = cb("focus_files"),

},

file_history_panel = {

["g!"] = cb("options"), -- Open the option panel

["<C-A-d>"] = cb("open_in_diffview"), -- Open the entry under the cursor in a diffview

["zR"] = cb("open_all_folds"),

["zM"] = cb("close_all_folds"),

["j"] = cb("next_entry"),

["<down>"] = cb("next_entry"),

["k"] = cb("prev_entry"),

["<up>"] = cb("prev_entry"),

["<cr>"] = cb("select_entry"),

["o"] = cb("select_entry"),

["<2-LeftMouse>"] = cb("select_entry"),

["<C-n>"] = cb("select_next_entry"),

["<C-p>"] = cb("select_prev_entry"),

["gf"] = cb("goto_file"),

["<C-w><C-f>"] = cb("goto_file_split"),

["<C-w>gf"] = cb("goto_file_tab"),

["<leader>e"] = cb("focus_files"),

["<leader>b"] = cb("toggle_files"),
},
option_panel = { ["<tab>"] = cb("select"), ["q"] = cb("close") },
},
})

git submodule harrsoncramer's settings, but how i from my side disable it? fugitive jump_next and jump_prev is what?

-- Gitsigns w/ hunks and blames.

vim.keymap.set("n", "<leader>ga", gitsigns.stage_hunk)

vim.keymap.set("n", "<leader>gb", gitsigns.blame_line)

vim.keymap.set("n", "<leader>gp", gitsigns.prev_hunk)

vim.keymap.set("n", "<leader>gn", gitsigns.next_hunk)

vim.keymap.set("n", "<leader>gr", gitsigns.reset_hunk)

vim.keymap.set("n", "<leader>gd", gitsigns.preview_hunk)

vim.keymap.set("n", "<leader>gq", gitsigns.setqflist("all")

  

return {

"ziontee113/icon-picker.nvim",

dependencies = { "stevearc/dressing.nvim" },

config = function()

require("icon-picker").setup({

disable_legacy_commands = true

})

vim.keymap.set("n", "<leader>e", ":IconPickerNormal<cr>")

for html tags

vim.keymap.set("n", "<leader>tn", ":tabnext<CR>")
vim.keymap.set("n", "<leader>tp", ":tabprev<CR>")
vim.keymap.set("n", "<leader>tc", ":tabclose<CR>")
![[Pasted image 20230225213617.png]]


