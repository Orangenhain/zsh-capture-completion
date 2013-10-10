# zsh-capture-completion

This is a proof of concept script for capturing completion matches generated by
the zshcompsys completion system. Because of the very complicated nature of
zsh's completions, this can (to my knowledge) not be done in a straightforward
way, and this script is accordingly hacky.


## Method

Roughly, a pseudo-interactive zsh session is spawned using zpty, and a buffer
string plus a tab character is sent so the complete-word widget is executed. To
capture the hits, the compadd function is selectivly overridden in a local
.zshrc file, capturing matches by injecting a parameter and outputting matches
to stdout.


## Usage

Usage:

    capture.zsh bufferstring

Examples:

    capture.zsh 'vim -'
    capture.zsh 'vim --'
    capture.zsh 'vim --r'
    capture.zsh 'echo *('
    capture.zsh 'scp hostname:'

For an application of ths technique, check out
[vim-zsh-completion](https://github.com/Valodim/vim-zsh-completion).
