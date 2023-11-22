
" ================================================================================================
" = Extensions =====================================
" ================================================================================================
Plug 'tpope/vim-surround'
Plug 'preservim/nerdtree'
Plug 'vim-scripts/argtextobj.vim'
Plug 'easymotion/vim-easymotion'
Plug 'vim-scripts/ReplaceWithRegister'

" ================================================================================================
" = Basic settings =====================================
" ================================================================================================

" 粘贴板共享
set clipboard=unnamed
set clipboard+=ideaput

" 显示当前模式
set showmode
set showcmd


" 设置自动
set autoindent
" 记住历史操作200行
set history=200

" 行号设置----------------------
" 使用行号
set number

" 使用相对行号
" set relativenumber

" 搜索-------------------------------
" 边输入边搜索(搜索时跳到目标出)
set incsearch
" 搜索高
set hlsearch

set highlightedyank

" 搜索大小写不敏感
set smartcase
"set ignorecase

" 滚动时保持上下边距
set scrolloff=5

" https://github.com/JetBrains/ideavim/blob/master/doc/ideajoin-examples.md
set wrap
set ideajoin

" set keep-english-in-normal-and-restore-in-insert
set visualbell
set surround
set commentary
set cursorline
set quickscope
set argtextobj

set multiple-cursors

" ================================================================================================
" = No Leader Keymaps =====================================
" ================================================================================================

" replaceWithRegister configuration  (替换操作不会替换寄存器: rs + (i/a) 操作对象
" https://github.com/JetBrains/ideavim/blob/master/doc/IdeaVim%20Plugins.md
nmap rs  <Plug>ReplaceWithRegisterOperator
xmap rs  <Plug>ReplaceWithRegisterVisual
" 替换一整行
nmap rss <Plug>ReplaceWithRegisterLine

nmap ge <action>(GotoNextError)
nmap gm <action>(MethodUp)
" 跳转被实现的类或方法
nmap gt <action>(GotoDeclaration)
"找到被实现的类或方法
nmap gp <action>(GotoSuperMethod)
"找到实现的方法所在的父类（接口）
nmap gi <action>(GotoImplementation)
" last changed in current buffer(file)
nmap ga '.

" multiple map 多光标操作
nmap <A-n> <Plug>NextWholeOccurrence
xmap <A-n> <Plug>NextWholeOccurrence
nmap g<A-n> <Plug>NextOccurrence
xmap g<A-n> <Plug>NextOccurrence
nmap <A-x> <Plug>SkipOccurrence
xmap <A-x> <Plug>SkipOccurrence
nmap <A-p> <Plug>RemoveOccurrence
xmap <A-p> <Plug>RemoveOccurrence

" bookmark in whole program  mark操作编辑
nmap ma <action>(ToggleBookmark)
nmap mb mB
nmap 'b `B
nmap mc mC
nmap 'c `C
nmap ms mS
nmap 's `S
nmap md mD
nmap 'd `D
nmap mf mF
nmap 'f `F

" 标签页切换
nmap L <action>(NextTab)
nmap H <action>(PreviousTab)

" 可视化模式下，选中行可以上下移动
vmap J <action>(MoveLineDown)
vmap K <action>(MoveLineUp)

" 找到上一个或下一个突出高亮
nmap <C-j> <Action>(GotoNextElementUnderCaretUsage)
nmap <C-k> <Action>(GotoPrevElementUnderCaretUsage)

" git
" show currentFile gitActions
nmap \] <ESC>:action Git.MainMenu.FileActions<CR>
" rollback selected   changed lines
vmap gr <action>(Vcs.RollbackChangedLines)zz

" show next changed
nnoremap [c :action VcsShowPrevChangeMarker<cr>
" show pre changed
nnoremap ]c :action VcsShowNextChangeMarker<cr>

" quickScope 按下下列字符时才高亮显示 Trigger a highlight in the appropriate direction when pressing these keys:
let g:qs_highlight_on_keys = ['f', 'F', 't', 'T']

" ================================================================================================
" = Leader Keymaps ===================================== " ================================================================================================
" leaderkey
let mapleader=" "

" ================================================================================================
" 👻👻👻 Which-Key 👻👻👻
" ================================================================================================
set which-key
set notimeout
set easymotion

" GIT ⭐️
" Vcs
nmap <leader>git <ESC>:action Git.Branches<CR>

" d: show git history
nmap <leader>dd <action>(Vcs.ShowTabbedFileHistory)

" shelf
nmap <leader>sf <action>(Vcs.Show.Shelf)

" 粘贴上次复制的内容
nmap <leader>py "0p

" f: Find/Format ⭐️
let g:WhichKeyDesc_FindOrFormat = "<leader>f FindOrFormat"
let g:WhichKeyDesc_FindOrFormat_FindFile = "<leader>ff FindFile"
nmap <leader>ff <action>(GotoFile)

let g:WhichKeyDesc_FindOrFormat_FindFileLocation = "<leader>fl FindFileLocation"
nmap <leader>fl <action>(SelectInProjectView)

let g:WhichKeyDesc_FindOrFormat_FindText = "<leader>ft FindText"
nmap <leader>ft <action>(FindInPath)

let g:WhichKeyDesc_FindOrFormat_Commands = "<leader>fc Commands"
nmap <leader>fc <action>(GotoAction)

let g:WhichKeyDesc_FindOrFormat_OpenedProject = "<leader>fp OpenedProject"
nmap <leader>fp <action>(OpenProjectWindows)

let g:WhichKeyDesc_FindOrFormat_Format = "<leader>fm Format"
nmap <leader>fm <action>(ReformatCode) \| <action>(OptimizeImports)

" i: Insert ⭐️
let g:WhichKeyDesc_InsertAfterBrackets = "<leader>i InsertAfterBrackets"
nmap <leader>i f(a

" j: add Semicolon and goto nextline⭐️
let g:WhichKeyDesc_InsertSemicolon = "<leader>j InsertSemicolon";;
nmap <leader>j A;<ESC>o

" l: lsp: Language server protocol (align with neovim)⭐️
let g:WhichKeyDesc_LSP = "<leader>l LSP"
let g:WhichKeyDesc_LSP_Rename = "<leader>lr Rename"
nmap <leader>lr <action>(RenameElement)

" n: No ⭐️
let g:WhichKeyDesc_No_Highlight = "<leader>nl NoHighlight"
nmap <leader>nl :nohlsearch<CR>

" 增加final
let g:WhichKeyDesc_No_Highlight = "<leader> final"
nmap <leader>fin Ifinal <ESC>f=

" 参数增加final
nmap <leader>pfin viacfinal <ESC>p

" s: Show ⭐️
let g:WhichKeyDesc_Show = "<leader>s Show"
let g:WhichKeyDesc_Show_FileStructure = "<leader>ss ShowFileStructure"
nmap <leader>ss <action>(FileStructurePopup)
let g:WhichKeyDesc_Show_Bookmarks = "<leader>sb ShowBookmarks"
nmap <leader>sb <action>(ShowBookmarks)
" 显示接口参数信息
nmap <leader>sp <action>(ParameterInfo)

" r: Run/Re ⭐️
let g:WhichKeyDesc_RunOrRe = "<leader>r RunOrRe"
let g:WhichKeyDesc_RunOrRe_ReRun = "<leader>rr ReRun"
nmap <leader>rr <action>(Rerun)
let g:WhichKeyDesc_RunOrRe_ReRunTests = "<leader>rt ReRunTests"
nmap <leader>rt <action>(RerunTests)
let g:WhichKeyDesc_RunOrRe_Rename = "<leader>rn Rename"
map <leader>rn <action>(RenameElement)

" w: Window ⭐️
let g:WhichKeyDesc_Windows_closeActiveWindow = "<leader>wc closeActiveWindow"
nmap <leader>wc <c-w>c

" z: zip(fold) ⭐️ 代码展开与关闭
let g:WhichKeyDesc_Zip = "<leader>z Zip"
let g:WhichKeyDesc_Zip_unZipAll = "<leader>zo unZipAll"
nmap <leader>zo <action>(ExpandAllRegions)
let g:WhichKeyDesc_Zip_ZipAll = "<leader>zc ZipAll"
nmap <leader>zc <action>(CollapseAllRegions)

" 返回上次跳转位置
nmap <leader>b <action>(Back)
" 恢复返回上次跳转位置
nmap <leader>fw <action>(Forward)

" 代码包裹一层
vmap <leader>lw <action>(SurroundWith
" 展示错误提示
nmap <leader>le <action>(ShowErrorDescription)

" 翻译
xmap <leader>t <Action>($EditorTranslateAction)<Esc>
nmap <leader>T <Action>($ShowTranslationDialogAction)
nmap <leader>t viw<Action>($EditorTranslateAction)


" e: Toggle Explorer ⭐️
nmap <leader>e <action>(ActivateProjectToolWindow)

" e: Extract
" extract method/function
vmap <leader>em <action>(ExtractMethod)<ESC>
" extract constant
vmap <leader>ec <action>(IntroduceConstant)
" extract field
vmap <leader>ef <action>(IntroduceField)
" extract variable
vmap <leader>ev <action>(IntroduceVariable)

" debug 模式运行命令
vmap <leader>dr <Action>(EvaluateExpression)


" 分屏操作(多窗口操作)
" 由于VimScript中的注释以一个双引号开始，有时容易与
" 双引号字符串中的双引号混淆(有些命令后不能跟注释，因为
" 字符串优先于注释)，因此，可在命令行后面的注释前加上
" 命令分隔符|(用于分隔放在单行上的多条Ex命令语句)，以免出错
noremap ,c <C-W>c  |" 关闭窗口
noremap ,s <C-W>s  |" 水平分割窗口
noremap ,v <C-W>v  |" 垂直分割窗口
noremap ,h <C-W>h  |" 将光标移到左边窗口
noremap ,j <C-W>j  |" 将光标移到下边窗口
noremap ,k <C-W>k  |" 将光标移到上边窗口
noremap ,l <C-W>l  |" 将光标移到右边窗口
noremap ,w <C-W>w  |" 将光标移到下一个窗口
" 左右比例控制
nmap <C-left> <action>(StretchSplitToLeft)
nmap <C-right> <action>(StretchSplitToRight)
" 上下比例控制
nmap <C-up> <action>(StretchSplitToTop)
nmap <C-down> <action>(StretchSplitToBottom)

" c: Close ⭐️;
nmap <leader>c :q!<CR>
" 重新打开关闭窗口
nmap sr <action>(ReopenClosedTab)
" 关闭除了激活窗口以外的窗口
nmap so <action>(CloseAllEditorsButActive)
