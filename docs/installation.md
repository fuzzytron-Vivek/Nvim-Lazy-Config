# Install Process and Initial Debugging.
--
### Installing using the Kickstart 
--
Change cwd to my `~/.config` folder and clone the neovim repo inside of the `~/.config` directory.


recommended step(if you're interested in working on your custom config some day) fork a clone of the source tree onto your personal account.
(my branch : lazy).

I followed the instructions mentioned on https://github.com/nvim-lua/kickstart.nvim in order to get the config installation done. 
(do checkout the installation recipe repo once in order to gain a better gauge of the prerequisites.

LINK: https://github.com/nvim-lua/kickstart.nvim 
)
### Missing LazyVim starter script
--
PROBLEM : my lazyvim config was not installed properly.

SOLUTION:
- Opened : https://www.lazyvim.org/installation 
- backed up my current config 
- cloned the starter script 
- and restarted neovim to find lazyvim working .

OBSERVATION:
let lazyvim install the required plugins and faced errors in installing the tree-sitter.


### Tree-sitter Version Conflict 
--

PROBLEM: had a version mismatch and had to re-install the latest version of tree-sitter

SOLUTION:


 `npm install -g tree-sitter-cli@latest `


### npm Root Access Problem
--
PROBLEM: EACCES Error

![TERMINAL MOCK-UP](~/.config/nvim/docs/assets)

SOLUTION:
By default, npm install -g (global install) tries to put files into a system directory (/usr/lib/node_modules/...) that's owned by root,
not by your regular user account (v).Unless we run sudo , npm will be denied permission to create the folder.

Since accessing and using commands from root is an unsafe practice , I proceeded to make the following changes and changing the default access location of npm to a place on my home directory 

I ran the following commands that create a directory for npm in the home directory and change the default path of npm from `root` to `.npm-global`: 

` mkdir -p ~/.npm-global
 npm config set prefix '~/.npm-global'
 echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
 source ~/.bashrc
 npm install -g tree-sitter-cli@latest `


ALTERNATIVE : Rust native `cargo` installer.






