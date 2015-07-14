# brew list on OSX Yosemite

* Vim에서 ctags를 사용할때 emacs의 ctags가 아닌 exuberant 사용하기
		brew install ctags-exuberant
		which -a ctags
			/usr/bin/ctags ==> original ctags
			/usr/local/bin/ctags ==> exuberant ctags
	Tell OSX to use Exuberant CTAGS
	Now, we just tell OSX which ctags to use by adding this to your .bash_profile:
			export PATH="/usr/local/bin:$PATH"
