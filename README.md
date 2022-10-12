https://user-images.githubusercontent.com/87373293/195375266-3b0c9f2b-ee42-4bd7-988f-7d633c474db1.mp4

### System

This aims to be a daily drivable Rust programming setup with window transparency

+ **OS, wm, bar**: Arch Linux + [Sway](https://github.com/swaywm/sway) + [Waybar](https://github.com/Alexays/Waybar)
+ **Font**: [Cascadia Code](https://github.com/microsoft/cascadia-code) + [Font Awesome](https://github.com/FortAwesome/Font-Awesome)
+ **Terminal**: [Alacritty](https://github.com/alacritty/alacritty)
+ **Shell, prompt**: Zsh + [Oh-My-Zsh](https://github.com/ohmyzsh/ohmyzsh) + [Starship](https://github.com/starship/starship)
+ **Editor**: [Neovim](https://github.com/neovim/neovim) + init.lua: [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) + [Lualine](https://github.com/nvim-lualine/lualine.nvim) + custom [base16 nvim](https://github.com/wincent/base16-nvim) theme
+ **Browser**: Firefox 99b6 (for [gif transparency glitch](https://bugzilla.mozilla.org/show_bug.cgi?id=1758975)), kiosk mode
+ **Browser extension**: [Stylus](https://github.com/openstyles/stylus) (for userstyles)
+ **Rustdoc style**: custom css userstyle (colors, sidebar on the right)
+ **Wallpaper**: [mpvpaper](https://github.com/GhostNaN/mpvpaper) + video made with [ffmpeg frame interpolation](https://ffmpeg.org/ffmpeg-all.html#minterpolate)

[Dotfiles](https://github.com/gergo-salyi/system-theme-001-rust-workstation)

### Wallpaper

+ Video [here](https://mega.nz/file/04dUCCIA#_YugW77rsZW4U9J9OB9_C6o_xNi04GgDStfYoYpIibQ), loops from 3.000 s inital offset for 17.000 s duration
+ Run with mpvpaper:

`mpvpaper -o "--ab-loop-a=3 --ab-loop-b=20" HDMI-A-1 ~/Videos/wallpaper-video.mp4`

+ It was made by screenshoting keyframes from (spoilers!) [this clip](https://www.youtube.com/watch?v=svBjMEhrjbk) at 1:06, repeating them to get a total of 25 jpg, then running:

`ffmpeg -framerate 1 -pattern_type glob -i '*.jpg' -filter:v "minterpolate" -r 60 -c:v libx264 -preset slow -pix_fmt yuv420p wallpaper-video.mp4`

### Rustdoc (WIP)

+ Needs [Firefox 99b6](https://download-installer.cdn.mozilla.net/pub/firefox/releases/96.0b6/linux-x86_64/en-US/) or older (a version without [commit e0938f086f24](https://hg.mozilla.org/mozilla-central/rev/e0938f086f2401b9589f6b98c9a0ac30e67e487a))
+ Make a dedicated profile: firefox-99b6
+ Install [Stylus](https://github.com/openstyles/stylus) exension and apply [this userstyle](https://github.com/gergo-salyi/system-theme-001-rust-workstation/blob/master/rustdoc-userstyle.css) to URLs `*://localhost:8000/*` and `*://localhost:8001/*`
+ Start local rustdoc servings and Firefox 99b6 with our profile in kiosk mode - from the rust project root dir run [this script](https://github.com/gergo-salyi/system-theme-001-rust-workstation/blob/master/.local/bin/rustdoc-local)
+ Then switch Firefox from kiosk fullscreen to a normal window with the wm's hotkey (eg. mod+f) 
+ Switch between the std doc tab and the crates doc tab with Crtl+Tab

The userstyle more-or-less works on doc.rust-lang.org and on docs.rs too
