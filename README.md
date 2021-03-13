# lf-scripts

Here I have scipts that help me get image previews in lf using ueberzug in alacritty. You just need to save the files into your system path and add the previewer inside the lf preview setting.

Programs needed:
- tar (tar info)
- zipinfo
- unrar
- glow (markdown previewer)
- 7z
- w3m
- ffmpeg
- ueberzug
- ghostscript (for pdf preview)
- mediainfo
- imagemagick
- [epub-thumbnailer](https://github.com/marianosimone/epub-thumbnailer)
- highlight

I use a wide variety of programs to have preview for almost every filetype but it is very simple to go and just remove them.

You can also add this inside you zsh config to run lf automatically with image preview support.

~~~
lf () {
	LF_TEMPDIR="$(mktemp -d -t lf-tempdir-XXXXXX)"
	LF_TEMPDIR="$LF_TEMPDIR" lf-run -last-dir-path="$LF_TEMPDIR/lastdir" "$@"
	if [ "$(cat "$LF_TEMPDIR/cdtolastdir" 2>/dev/null)" -eq 1 ]; then
		cd "$(cat "$LF_TEMPDIR/lastdir")"
	fi
	rm -r "$LF_TEMPDIR"
	unset LF_TEMPDIR
}
~~~

Add this to your lfrc

~~~
set preview true
set previewer lf-previewer
set cleaner lf-cleaner
~~~
