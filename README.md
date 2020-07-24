<div align='center'>
  <br /><br /><br />
  <img src='https://raw.githubusercontent.com/mhinz/vim-galore/master/static/images/logo-vim-galore.png' alt='vim-galore logo' />
  <br /><br /><br /><br />
  <div>
    <a href='https://github.com/wsdjeg/vim-galore-zh_cn'>Chinese</a> |
    <a href='http://postd.cc/?s=vim-galore'>Japanese</a> |
    <a href='https://github.com/lsrdg/vim-galore'>Portuguese</a> |
    <a href='http://givi.olnd.ru/vim-galore/vim-galore-ru.html'>Russian</a>
    <div>
      <br />
      <sub>Licensed under <a href='https://creativecommons.org/licenses/by-sa/4.0'>CC BY-SA 4.0<a/>.</sub>
    </div>
  </div>
  <br /><br />
</div>

### [소개](#intro-1)

- [Vim이란?](#what-is-vim)
- [Vim의 철학](#the-vim-philosophy)
- [처음 시작하기](#first-steps)
- [vimrc의 시작](#minimal-vimrc)
- [어떤 종류의 Vim을 나는 사용하고 있는가?](#what-kind-of-vim-am-i-running)
- [치트셋(컨닝 페이퍼)](#cheatsheets)

### [기초](#basics-1)

- [버퍼, 윈도우, 탭](#buffers-windows-tabs)
- [활성된, 로드된, 목록화된, 이름있는 버퍼](#active-loaded-listed-named-buffers)
- [변수 목록](#argument-list)
- [맵핑](#mappings)
- [맵리더](#mapleader)
- [레지스터](#registers)
- [범위](#ranges)
- [지점](#marks)
- [자동완성](#completion)
- [모션, 연산자, 텍스트 객체](#motions-operators-text-objects)
- [자동 명령어](#autocmds)
- [변경 목록, 이동 목록](#changelist-jumplist)
- [Undo 트리](#undo-tree)
- [Quickfix(빠른수정)와 location(위치) 목록](#quickfix-and-location-lists)
- [매크로](#macros)
- [Colorschemes](#colorschemes)
- [Folding](#folding)
- [Sessions](#sessions)
- [Locality](#locality)

### [Usage](#usage-1)

- [Getting help offline](#getting-help-offline)
- [Getting help offline (alternative)](#getting-help-offline-alternative)
- [Getting help online](#getting-help-online)
- [Autocmds in practice](#autocmds-in-practice)
  - [User events](#user-events)
  - [Nested autocmds](#nested-autocmds)
- [Clipboard](#clipboard)
  - [Clipboard usage (Windows, macOS)](#clipboard-usage-windows-macos)
  - [Clipboard usage (Linux, BSD, ...)](#clipboard-usage-linux-bsd-)
- [Restore cursor position when opening file](#restore-cursor-position-when-opening-file)
- [Temporary files](#temporary-files)
  - [Backup files](#backup-files)
  - [Swap files](#swap-files)
  - [Undo files](#undo-files)
  - [Viminfo files](#viminfo-files)
  - [Example configuration for temporary files](#example-configuration-for-temporary-files)
- [Editing remote files](#editing-remote-files)
- [Managing plugins](#managing-plugins)
- [Block insert](#block-insert)
- [Running external programs and using filters](#running-external-programs-and-using-filters)
- [Cscope](#cscope)
- [MatchIt](#matchit)
- [True colors](#true-colors)

### [Tips](#tips-1)

- [Go to other end of selected text](#go-to-other-end-of-selected-text)
- [Saner behavior of n and N](#saner-behavior-of-n-and-n)
- [Saner command-line history](#saner-command-line-history)
- [Saner CTRL-L](#saner-ctrl-l)
- [Disable audible and visual bells](#disable-audible-and-visual-bells)
- [Quickly move current line](#quickly-move-current-line)
- [Quickly add empty lines](#quickly-add-empty-lines)
- [Quickly edit your macros](#quickly-edit-your-macros)
- [Quickly jump to header or source file](#quickly-jump-to-header-or-source-file)
- [Quickly change font size in GUI](#quickly-change-font-size-in-gui)
- [Change cursor style dependent on mode](#change-cursor-style-dependent-on-mode)
- [Don't lose selection when shifting sidewards](#dont-lose-selection-when-shifting-sidewards)
- [Reload a file on saving](#reload-a-file-on-saving)
- [Smarter cursorline](#smarter-cursorline)
- [Faster keyword completion](#faster-keyword-completion)
- [Cosmetic changes to colorschemes](#cosmetic-changes-to-colorschemes)

### [Commands](#commands-1)

- [:global and :vglobal](#global-and-vglobal) - Execute a command on all matching lines.
- [:normal and :execute](#normal-and-execute) - The scripting dream team.
- [:redir and execute()](#redir-and-execute) - Capture command output.

### [Debugging](#debugging-1)

- [General tips](#general-tips)
- [Verbosity](#verbosity)
- [Profiling startup time](#profiling-startup-time)
- [Profiling at runtime](#profiling-at-runtime)
- [Debugging Vim scripts](#debugging-vim-scripts)
- [Debugging syntax files](#debugging-syntax-files)

### [Miscellaneous](#miscellaneous-1)

- [Additional resources](#additional-resources)
- [Vim distributions](#vim-distributions)
- [Standard plugins](#standard-plugins)
- [Map CapsLock to Control](#map-capslock-to-control)
- [Generating HTML from buffer](#generating-html-from-buffer)
- [Easter eggs](#easter-eggs)
- [Why hjkl for navigation?](#why-hjkl-for-navigation)

### [Common problems](#common-problems-1)

- [Editing small files is slow](#editing-small-files-is-slow)
- [Editing huge files is slow](#editing-huge-files-is-slow)
- [Bracketed paste (or why do I have to set 'paste' all the time?)](#bracketed-paste-or-why-do-i-have-to-set-paste-all-the-time)
- [Delays when using escape key in terminal](#delays-when-using-escape-key-in-terminal)
- [Function search undo](#function-search-undo)

### [Technical quirks](#technical-quirks-1)

- [Newline used for NUL](#newline-used-for-nul)

### [Terminology](#terminology-1)

- [Vim script? Vimscript? VimL?](#vim-script-vimscript-viml)

### [List of colorschemes](PLUGINS.md#colorschemes-1)

### [List of plugins](PLUGINS.md)

<br>

# Intro

## What is Vim?

[Vim](http://www.vim.org)은 1991년에 [Bram
Moolenaar](https://en.wikipedia.org/wiki/Bram_Moolenaar)이 만든 텍스트 편집기이다.
Vim은 [qed](https://en.wikipedia.org/wiki/QED_(text_editor))와 조상을 같이하는 텍스트 에디터의 한 부류이다.

Vim과 관련된 프로젝트는 [vim.org](http://www.vim.org/index.php)에서 찾아볼 수 있다..

Vim 받기: 패키지 매니저를 이용하거나 vim.org의 [다운로드 페이지](http://www.vim.org/download.php)를 방문하여
다운받을 수 있다.

Vim과 관련된 질문이나 토론은 
[vim_use](https://groups.google.com/forum/#!forum/vim_use) 메일링 목록을 이용하거나 
`#vim` 채널의 IRC ([Freenode](https://freenode.net)) 사용할 수 있다..
 
현재 개발은 [Vim 깃헙](https://github.com/vim/vim)에서, 개발과 관련된 토론은 주로
[vim_개발자](https://groups.google.com/forum/#!forum/vim_dev) 메일링 리스트로 사용된다.

Vim과 관련된 잘못된 상식을 타파하기위해 아티클
[왜 오타쿠같지만 천재인 그들은 vim을 사용하는가?](http://www.viemu.com/a-why-vi-vim.html)을 읽어보자

## The Vim Philosophy

Vim은 양식편집(modal editing)의 철학을 고수한다. 이 의미는 주어진 양식(mode)에 따라
키의 용도가 다르게 변한다는 것이다. 일반모드로 파일을 둘러보고, 삽입모드로 문자를 넣을 수 있으며,
비주얼 모드로 단락을 선택할 수 있고, 명령어 모드로 다양한 명령어를 실행하는 식의 형태이다.
복잡하게 들릴 수 있지만, 이 것이 굉장한 장점인 이유는, 다양한 키 조합을 줄여주고, Vim을 사용하는
대부분의 시간동안 키 하나를 누룬 후 다른 키를 누르는 간단한 방식으로 만들어 준다. 이 때문에 더 자주 사용되는
기능은 더 적은 키 조합이 필요하게 된다.

일례로, 연산자(_Operators_)와 그 동작(_motion_)이 양식편집과 잘 맞는 컨셉 중 하나이다.
연산자는 하나의 액션으로 시작을 한다(가령, 텍스트를 선택/삭제/변경하는 액션). 그 다음,
한 동작을 원하는 텍스트의 영역을 지정한다. 괄호 안의 모든 텍스트를 변경하기 위해서, `ci(`(change inner parentheses)를
사용해보라. 전제 단락을 지우기 위해서 `dap`(delete around parentheses)를 사용해보라. 

만약 고수가 사용하는 vim을 보면, 그들을 아마도 vim언어를 사용한 것이고 또한 그들의 손은
피아니스트처럼 움직일 것이다. 심지어 복잡한 기능마저도 몇 번의 키를 누름으로써 해결된다.
그들은 더 이상 어떤 키를 눌러야 하는 것초자 생각하지 않게된다. 왜냐면, 그것들은 이미 
[muscle memory](https://en.wikipedia.org/wiki/Muscle_memory)에서 일어나기 때문이다.
이것은 [인지부하(cognitive
load)](https://en.wikipedia.org/wiki/Cognitive_load) 낮추어 주며 작업자체를 몰두하도록 도와준다.

## First steps

Vim이 설치될때 기본적으로 당신이 알아야 할 것들에 대해 튜토리얼이 같이 설치됩니다. 아래 명령어를
shell에 실행하세요(영어임)
```
$ vimtutor
```
읽는 것은 겉보기에 지루할 수 있으니 연습으로 시작하세요. 당신이 일반적으로 사용한 텍스트 편집기는
아마 양식편집용이 아닐 수 있고, 따라서 Vim의 시작이 생각보다 이상하다고 생각할 수 있습니다. 그러나,
Vim을 사용하면 할 수록 이것은 당싱의 [muscle memory](https://en.wikipedia.org/wiki/Muscle_memory)가 됩니다.

Vim은 vi 클론 중 하나인 [Stevie](https://en.wikipedia.org/wiki/Stevie_(text_editor))에
올라가 두가지 기능(호환모드와 비호환 모드)을 지원한다. 호환 모드는 Vim의 기본 옵션 대신
vi의 모든 옵션을 기본으로 갖는 모드 이다. 즉, 직업 사용자 vimrc를 생성하거나 시작을 `vim -N`으로
하지 않는한, 호환모드는 기본적으로 적용이 된다. 제발, vim을 호환모드로 사용하지 말길 권한다.

다음 단계:

1. 당신만의 [vimrc](#minimal-vimrc) 생성하기.
2. 첫 주동안 당신만의 [치트셋](#cheatsheets)을 준비하기.
3. [기본기능](#basics-1)을 참조하여 가능한 기능들을 둘러보기.
4. 필요할때 배우세요!. 아마도 절대로 Vim배우기가 끝나지 않을 수 있습니다. 
   만약 어떤 문제가 생기면, 바로 인터넷으로 찾아보세요. 직면한 문제는 이미 풀렸을 거에요.
   Vim은 잘 정의된 문서가 함께 설치되니, 둘러보는 방법을 배우는 것이 정말 중요합니다.
   [오프라인으로 도움얻기](#getting-help-offline).
5. 한번 [추가 문서들](#additional-resources)도 둘러 보세요.

마지막 충고: 제발 먼저 한번 Vim을 제대로 배우세요. 다양한 [플러그 인](#managing-plugins)
에서 제공하는 기능들이 이미 Vim에서 제공할 수도 있어요.

## Minimal vimrc

사용자 vimrc는 `~/.vimrc`나 혹은 더 분리된 공간을 위해 `~/.vim/vimrc`에 저장합니다.
후자의 경우에 Github과 같은 version control 시스템에 넣어 사용하기 편합니다.

인터넷에 최소화 버전의 다양한 vimrc파일들이 발견되는데, 아마도 제 버전은 그렇게나
작은 버젼이 아닐수 있어요. 하지만 시작하기에 좋은 기능들을 많이 넣어 놓았습니다.

결국, 스스로 전부 읽어보고 결정해야 겠지만요 ㅎ.

이곳에 다양한 vimrc: [minimal-vimrc](static/minimal-vimrc.vim)

그리고 혹시 제가 만들은 것에 관심이 가시면:
[내 vimrc](https://github.com/mhinz/dotfiles/blob/master/.vim/vimrc).

**TIP**: 대부분의 플러그인을 만든 사람들은 여러가지 플러그인을 유지보수하고, 자신만의
vimrm를 깃헙에 올려놉니다.(종종 vim-config란 폴더나 dotfiles이란 폴더 이름을 사용해요).
따라서, 좋아하는 플러그인을 찾으면, 그 사람들의 깃헙 페이지를 찾아보세요.

## What kind of Vim am I running?

`:version`을 입력하면, 현재 설치되어 있는 Vim에 대한 모든 정보를 찾아볼 수 있습니다.

첫 줄에 7.4와 같은 버전정보와 언제 컴파일이 된 바이너리인지를 알려줍니다.
다음 줄은 `Included patches: 1-1051`처럼 시작하는데, 패치 레벨을 알려주는 정보 입니다.
따라서 당신의 정확한 버전은 7.4.1051이 됩니다.

다음 줄에선 `Tiny version without GUI` 혹은 `Huge version with GUI`으로 시작하는데,
가장 쉽게 알아볼 수 있는 정보 중 하나는 GUI기능을 제공하는가 입니다. 예를들면, `:gui`를 
Vim에 입력하거나 쉘에 gvim을 입력해 봅니다. 다른 중요한 정보중의 하나는 `Tiny`와
`Huge`입니다. Vim은 기능들을 셋으로 묶어 두었는데 `tiny`, `small`, `normal`, `big`,
그리고 `huge`가 기능 셋들을 지칭하는 용어 입니다.

대부분의 `:version` 결과는 기능목록로 차지합니다.
`+clipboard`은 클립보드기능이 들어간 것이고, `-clipboard`은 클립보드 기능이 빠진 것입니다.

몇 가지의 Vim 기능들은 이런 기능들이 들어가야만 작동을 합니다.
`:prof`를 사용하기 위해선, 이것은 `+profile`기능을 사용하기 때문에 Huge 기능 셋이 들어간
vim이 필요합니다.

만약에 패키지 매니져를 통해 설치한 Vim이 Huge셋이 아니면, 
`vim-x`, `vim-x11`, `vim-gtk`, `vim-gnome`혹은 이와 비슷한 이름으로 찾아보세요.
이들은 보통 Huge셋으로 설치되거든요.

혹은 아래로 프로그램을 만들어서 버젼을 확인 할 수도 있습니다.
```vim
" Do something if running at least Vim 7.4.42 with +profile enabled.
if (v:version > 704 || v:version == 704 && has('patch42')) && has('profile')
  " do stuff
endif
```

도움:

```
:h :version
:h feature-list
:h +feature-list
:h has-patch
```

## Cheatsheets

- http://people.csail.mit.edu/vgod/vim/vim-cheat-sheet-en.png
- https://cdn.shopify.com/s/files/1/0165/4168/files/preview.png
- http://michael.peopleofhonoronly.com/vim/vim_cheat_sheet_for_programmers_screen.png
- http://www.rosipov.com/images/posts/vim-movement-commands-cheatsheet.png

혹은 Vim자체에서 치트셋을 보려면: [vim-cheat40](https://github.com/lifepillar/vim-cheat40).

# Basics

## Buffers, windows, tabs

Vim은 텍스트 편집기입니다. 텍스트가 보여질 때매다, 그 텍스트는 버퍼의 일부분
입니다. 각 파일은 또한 각기 자신만의 버퍼를 갖습니다. 플러그인 또한 자신들이
가진 버퍼를 이용해 결과르 보여줍니다.

**버퍼**들은 다양한 속성을 갖는데, 가령 그 버퍼가 가진 텍스트가 변경불가한 것인지 혹은
연결된 파일이 존재하는지, 혹은 그 파일에 따라 디스크에 저장이 되야하는지 등을 뜻합니다.

**윈도우**들은 버퍼 위를 바라보는 창들입니다. 만약 한 번에 여러 파일을 보거나 혹은
다른 장소에 저장된 같은 파일을 본다면, 그것은 윈도우를 사용하는 것입니다.

그리고, 제발 그것들을 _splits_라고 부르지 마세요.  You can split a window in two, but
that doesn't make them _splits_. (split은 명사가 아니니 splits라고 복수형으로 표현하지
말아 달라는 것입니다. 한국에서는 크게 무의미 하네요)

윈도우는 가로 혹은 세로로 갈라질 수 있으며, 또한 너비나 높이를 조절할 수 있습니다.
따라서, 어떤 레이아웃을 가진 윈도우도 당신이 원하는대로 사용할 수 있죠.

**탭 페이지** (혹은 그냥 탭) 은 윈도우들의 집합입니다. 따라서, 다양한 윈도우 레이아웃을
사용하고 싶다면, 탭을 사용하세요.

간단하게 말하면, 어떤 추가 변수 없이 Vim을 사용하면, 당신은 한 개의 윈도우를
갖고서 하나의 버퍼를 보여주는 한개의 탭을 갖게 될 것입니다.

그나저나, 버퍼 목록은 글로벌이며 어느탭이든지 접근 가능합니다.

## Active, loaded, listed, named buffers

`vim file1`처럼 Vim을 실행해 보세요. 파일의 내용이 버퍼에 채워질 것입니다.
이제 당신은 **로드된(loaded) 버퍼**를 갖고 있죠. 버퍼의 내용물은 이제 당싱이 Vim을 저장
시켜야 디스크에 저장될 것입니다.(파일에 쓴다는 소리죠)

버퍼는 윈도우에 보여지기 때문에, **활성된(active) 버퍼**입니다. 이제 다른 파일을
`:e file2`로 열어 보세요. `file1`은 이제 **숨겨진(hidden) 버퍼**이고 `file2`가 
활성화 됩니다.

이 두 버퍼 모두 **목록화(listed)**되어, 모두 `:ls`를 통해서 출력 됩니다.
플러그인 버퍼나 도움버퍼들 모두 목록화되지 않습니다. 왜냐면, 그 버퍼들은 편집기를
통해 변경하는 일반적인 파일들이 아니기 때문이죠. 하지만 이 두 가지 종류 버퍼를
모두 보려면 `:ls!`를 사용하세요.

플러그인이 종종 사용하는 **이름없는(unnamed) 버퍼**는 파일 이름이 없습니다.
예를 들면, `:enew`는 이름없는 빈 버퍼를 생성하는데, 그곳에 텍스트를 추가한 후에
`:w /tmp/foo`처럼 명령어를 사용해야 저장할 수 있습니다.

## Argument list

[글로벌 버퍼 목록](#buffers-windows-tabs)은 Vim이 가진 것이죠. 그전에, vi에는
변수 목록이 존재했는데, Vim 역시 그것을 갖고 있죠.

쉘에서 Vim에게 주어진 모든 파일 이름들은 이 변수 목록에 기억됩니다. 그리고 여러개의
목록들로 구성될 수도 있죠. 기본셋팅으로 모든 변수들은 글로벌 변수목록에 들어갑니다.
하지만 `:arglocal`로 새로운 변수목록을 생성하여 로컬 윈도우에서 사용할 수 있죠.


`:args`으로 현재 변수목록을 보세요. `:next`, `:previous`, `:first`, `:last`들을
통해서 변수 목록에 있는 다른 파일들로 바꾸어 보세요, `:argadd`, `:argdelete`로
변수목록을 바꾸어 보고  `:args`로 다시 확인해 보세요.

만약에 버퍼나 변수목록을 통해 작업을 하는 것은 완전히 당신의 자유입니다. 제 생각은
대부분의 사람들이 버퍼목록은 사용한다고 보죠.

그래도, 한 가지 변수목록이 사용되는 곳이 있습니다. 바로 `:argdo`를 통한 배치 프로세싱
입니다. 간단한 리팩토링 예를 보죠.

```vim
:args **/*.[ch]
:argdo %s/foo/bar/ge | update
```
이것은 현 폴더 혹은 그아래 있는 폴더에 있는 모든 .c나 .h파일에 나오는 'foo'를
'bar'로 바꿉니다.

도움: `:h argument-list`

## Mappings

당신은 또한 `:map`계열의 명령어로 새로운 맵핑을 정의 할 수 있습니다. 각 명령어
집군은 특정 모드를 위해 새로운 맵핑을 정의할 수 있습니다. 기술적으로, Vim은
12개의 모드가 있고, 그 중 6개가 맵핑될 수 있습니다. 추가로, 어떤 명령어들은 한
번에 여러가지 모드로 활성화될 수 있습니다.

| Recursive(재귀) | Non-recursive | Unmap     | Modes(모드)                      |
|-----------------|---------------|-----------|----------------------------------|
| `:map`          | `:noremap`    | `:unmap`  | normal, visual, operator-pending |
| `:nmap`         | `:nnoremap`   | `:nunmap` | normal(일반)                     |
| `:xmap`         | `:xnoremap`   | `:xunmap` | visual(비주얼)                   |
| `:cmap`         | `:cnoremap`   | `:cunmap` | command-line(명령어)             |
| `:omap`         | `:onoremap`   | `:ounmap` | operator-pending(지연된 연산자)  |
| `:imap`         | `:inoremap`   | `:iunmap` | insert(삽입)                     |

예) 아래는 일반모드만 맵핑을 새로 정의합니다.
E.g. this defines the mapping for normal mode only:

```vim
:nmap <space> :echo "foo"<cr>
```

맵핑 지우기: `:nunmap <space>`.

일반적이진 않지만 다른 모드들을 보려면 `:h map-modes`을 보세요.

좋아요. 아마도 배우려는 사람들에게 가장 혼동스런 부분이 남았어요.
바로 `:nmap`은 재귀적이라는 것이죠. 그 말은 두 번째 인자는 다른 맵핑을
고려한다는 거에요.

자. 아래와 같이 b로 Foo를 출력하는 맵핑을 정의한다고 해봅시다.

```vim
:nmap b :echo "Foo"<cr>
```

그러면 만약에 `b`(한단어 뒤로가기)의 기본적인 맵핍을 다른 키로 바꾸고 싶다면요?


```vim
:nmap a b
```

<kbd>a</kbd>를 누르면, 아마도 한 단어 뒤로가길 예상하겠지만, 
"Foo"가 명령어 창에서 출력이 될거에요. 왜냐면 `b`가 다른 행동을
하도록 이미 맵핑되어 있기 때문이죠. `:echo "Foo"<cr>`로요.

이 문제를 해결하기 위한 방법은 재귀방지용 맵핑을 대신 이용하는 것이죠.

```vim
:nnoremap a b
```

추천: 재귀적인 것을 예상하지 않는 이상 항상 재귀방지용 맵핑을 이용하세요. 

정의되어 있는 맵핑보려면 우측 인자를 넣지 않으면 됩니다. 예를들어, `:nmap`은 모든 일반
맵핑정보를 보여주고, `:nmap <leader>`은 맵리더(mapleader)가 들어간 모든 맵핑을 모여줍니다.

만약 기본 맵핑을 중지하고 싶다면, 특별한 문자인 `<nop>`을 이용해서
`:noremap <left> <nop>`처럼 맵핑을 생성하세요.
If you want to disable a standard mapping, map them to the special 
character, e.g. 

도음:

    :h key-notation
    :h mapping
    :h 05.3

## Mapleader

맵리더는 간단하게 맵핑키의 시작을 알리는 지시자에요. 이것은 보통 사용자지정
맵핑을 쓸때 사용되고 기본적으로 `\`으로 지정되어 있습니다.

```vim
nnoremap <leader>h :helpgrep<space>
```

이 맵핑은 `\h`으로 활성화됩니다. `<space>h`을 대신 사용하려면:

```vim
let mapleader = ' '
nnoremap <leader>h :helpgrep<space>
```

그리고, `<leader>`과 대비되어 `<localleader>`은 로컬에서 중요하게 작동합니다.
이것은 버퍼에 로컬로 붙어있는 맵핑에서 사용하게 되어있는데,
가령, 특별한 파일 종류에만 작동하는 플러그인들에서 볼수 있죠. 이것 또한
`\`을 기본으로 사용합니다.

**주의**: 맵리더를 맵핑하기 전에 지정하세요. 이미 사용되고 있는 다른 리더맵핑은 
변하세지 않습니다. 왜냐면 맵리더가 변경되었기 때문이죠.

<leader>`은 모든 맵리더로 시작하는 맵핑들을 보여줍니다. 그러니 당신만의 맵핑이
맞는지 재차 확인하며 사용하세요.

더 자세한 정보는 `:h mapleader`나 `:h maplocalleader`를 보세요.

## Registers

레지스터는 텍스트를 저장하는 공간입니다. 텍스트를 복사해서 레지스터에 넣는 것을
**복사-잡아넣기**(yanking)이라고 합니다. 그리고 레지스터에서 꺼내는 것을 **붙여넣기**(pasting)라고 하죠.

Vim은 아래와 같은 레지스터들을 제공합니다:


| 종류(Type)                | 문자(Character)              | Filled by? | Readonly? | Contains text from? |
|---------------------------|------------------------|------------|-----------|---------------------|
| 이름없는(Unnamed)            | `"`                    | vim        | [ ]       | 마지막 복사나 삭제. (`d`, `c`, `s`, `x`, `y`) |
| 숫자(Numbered)           | `0` to `9`             | vim        | [ ]       | 레지스터`0`: 마지막 복사. 레지스터`1`: 마지막 삭제. 레지스터`2`: 마지막 이전 삭제. 등. 레지스터 `1`-`9` 를 읽기만 가능한 9개로 구성된 [큐(queue)](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))로 생각하세요. |
| 작은삭제(Small delete)        | `-`                    | vim        | [ ]       | 한 줄보다 짧은 마지막 삭제. |
| 이름붙은(Named)               | `a` to `z`, `A` to `Z` | user       | [ ]       | 레지스터 `a`에 복사하면 그곳에 저장되어 있던 텍스를 대체합니다.  레지스터 `A`에 복사를 하면 기조의 `a`에 텍스트를 추가합니다. |
| 읽기만가능(Read-only)           | `:`, `.`, `%`          | vim        | [x]       | `:`: 마지막 명령어, `.`: 마지막으로 들어간 텍스트, `%`: 현재 파일 이름. |
| 대체버퍼(Alternate buffer)    | `#`                    | vim        | [ ]       | 일반적으로, 현재 윈도우에서 이전에 불러온 버퍼 부르기. 도움 `:h alternate-file` |
| 표현(Expression)          | `=`                    | user       | [ ]       | 복사된 값을 vim 표현식으로 해석 평가 합니다. 삽입 모드에서 `<c-r>=5+5<cr>`을 해보세요. "10"이 삽입 될것입니다. |
| 선택(Selection)           | `+`, `*`               | vim        | [ ]       | `*`와 `+`는 [클립보드(clipboard)](#clipboard) 레지스터입니다. |
| 드롭(Drop)                | `~`                    | vim        | [x]       | 마지막으로 드래그 앤 드랍한 것으로 부터. |
| 블랙홀(Black hole)          | `_`                    | vim        | [ ]       | 만약 그 어떤 레지스터로부터 영향받길 원하지 않는 다면. 예를 들어, `"_dd`은 레지스터에 영향 없이 라인을 지워 줄 것이에요. `"`, `1`, `+`, `*`. |
| 마지막검색패턴(Last search pattern) | `/`                    | vim        | [ ]       | `/`, `?`, `:global`과 사용된 마지막 패턴. |

읽기만 가능한 레지스터가 아니면, 사용자에 의해 지정이 가능합니다:
```vim
:let @/ = 'register'
```

그런후 <kbd>n</kbd>는 다음 저장된 레지스터로 이동할 것입니다.

많은 예외적인 경우로 레지스터들이 채워지는 경우가 있는습니다. `:h registers`를 확인해 보세요.

`y`로 복사를 하고, `p`/`P`로 붙여넣으세요. 하지만 또한 Vim은 문자단위와 줄단위의
비주얼 선택모드를 지원한다는 것도 염두하세요. `:h linewise`를 참고하세요.

**예제: 줄 단위**

`yy` (혹은 그냥 `Y`)로 현재 줄을 복사하시고, 커서를 다른 곳으로 옮기세요. 그리고 `p`를 사용해서
현재줄 아래 붙여넣거나, `P`로 줄 위로 붙여넣으세요.

**예제: 문자 단위**

`0yw`로 첫번째 단어를 복사한 후에, 커서를 다른데 옮기세요. 그리고 마찬가지로,
`p`를 사용해서 현재단어 뒤에 붙여넣거나, `P`로 앞에 붙여넣으세요.

**예제: 레지스터의 이름을 명시하기**

`"aY`로 현재의 줄을 복사해서 레지스터 `a`로 넣습니다. 다른 줄로 커서를 옮기세요.
`"AY`를 이용해서 현재줄을 이전에 채워둔 레지스터 `a`에 추가합니다..

지금까지 소개드렸던 레지스터들로 장난쳐보길 권해드려요. 
`:reg`를 사용하면 실제로 어떤 일들이 레지스터에 일어나는지도 볼 수 있어요.

**재미있는 사실**: Emacs에서는 "yanking(복사)"가 붙여넣기로 지정되어있죠.(정확히는
이전에 지워진 텍스트를 재삽입하는 것입니다)

## Ranges

범위(Ranges)는 꽤나 쉽게 이해할 수 있습니다. 하지만 많은 Vim 사용자들이 이것의 
끝판왕을 가보지 못했죠.

- 많은 명령어가 범위를 이용합니다.
- 하나의 주소는 특정한 줄을 가리키죠.
- 하나의 범위는 한개의 주소거나 한 `,`나 `;`의해 분리된 한 쌍이 주소 입니다.
- 범위들은 명령어에게 어떤 줄의 범위에서 일들이 일어나야하는지 알려줍니다.
- 일반적으로 명령어들은 현재의 라인에서만 실행되죠. 또한 잘 알려져 있는 예외적인 경우로는
모든 라인에서 일어나게 만드는 `:write`과 `:global`입니다.

범위의 사용법은 꽤나 직관적이고, 이 아래 몇 가지 예제를 넣었습니다. 
(`:d`는 `:delete`의 줄임말이에요)

| 명령어(Command) | 실행될 줄(Lines acted on) |
|---------|----------------|
| `:d` | 현재 줄. |
| `:.d` | 현재 줄. |
| `:1d` | 첫번째 줄. |
| `:$d` | 마지막 줄. |
| `:1,$d` | 모든 줄. |
| `:%d` | 모든 줄 (`1,$`를 한줄로 쓴 꿀팁). |
| `:.,5d` | 현재 줄부터 다섯 번째 줄. |
| `:,5d` | 역시 현재 줄부터 다섯 번째 줄. |
| `:,+3d` | 현재 줄부터 세 줄 추가까지. |
| `:1,+3d` | 첫 줄부터 현재 줄 + 3줄 까지. |
| `:,-3d` |  현재 줄부터 세 줄 이전까지. (Vim will prompt you, since this is a reversed range.) |
| `:3,'xdelete` | 세번째 줄부터[지점(mark)](#marks) x. |
| `:/^foo/,$delete` | 다음줄의 "foo"로 시작하는 글자 줄부터 마지막 줄까지. |
| `:/^foo/+1,$delete` | 다음줄의 "foo"로 시작하는 글자의 다음 줄부터 마지막 줄까지. |

`,` 대신 `;`이 범위를 분리하는 문자로 사용될 수 있는 것을 알아두세요. 차이점은
`부터,까지`를 사용하면 _까지_는 현재 줄에서 상대적인 곳입니다. 하지만 `부터;까지`를 
사용하면, _까지_는 _부터_에서 상대적인 곳에요! 당신이 5번째 줄에 있으면, `:1,+1d`는 1부터
6까지 지웁니다. 하지만 `:1;+1d`는 1과 2만 지워버리죠.

`/` 주소는 다른 주소 앞에 선행 될 수 있습니다. 이것은 _스택_ 패턴을
사용할 수 있게 만들어주죠.

```vim
:/foo//bar//quux/d
```
이것은 현재줄 이후로 "foo"와 "bar" 나온 후 "quux"이 나온 줄을 지워버립니다.

때론, Vim은 자동으로 범위를 명령어에 붙여버리죠. 예를 들면, `V`를 눌러 시각모드를
선택하고, 몇 줄을 선택한 후에 `:`을 넣으세요. 커맨드라인은 자동으로 범위를 지정한
`'<,'>`으로 늘어날거에요. (이것은 또한 당신이 가끔 `:vnoremap foo :<c-u>command`과 같은
맵핑을 보는 이유기도 합니다. 여기서 `<c-u>`는 범위를 지우기위해서 사용합니다. 왜냐면,
Vim은 범위를 지정하지 않는 명령어에 범위를 넣으면 오류를 표시하기 때문이죠.)

다른 예로는 일반모드에서 `!!`을 사용하는 것이죠. 이것은 명령줄에 `:.!`를 넣습니다.
만약에 외부 프로그램과 같이 사용되면, 그 프로그램의 결과값이 현재 줄에 붙여집니다.
그래서 당신은 현재줄에 ls의 결과값도 `:?^$?+1,/^$/-1!ls`을 사용해서 넣을 수 있죠. 대박!


도움:

```
:h cmdline-ranges
:h 10.3
```

## Marks

You use marks to remember a position, that is line number and column, in a file.
지점은 한 파일에서 줄번호(line number)와 문자줄(column)로 위치를 기억할 수 있습니다.

| 지점들(Marks) | 누가 지정(Set by..) | 사용법(Usage) |
|-------|----------|-------|
| `a` - `z` | User | 로컬에서 파일로, 따라서 한 파일안에서만 유효함. 한 소문자 지점으로 이동하는 것은 현재 파일 안에서 이동하는 것을 의미한다. |
| `A` - `Z` | User | 글로벌, 따라서 이것은 파일간에도 유효하다. 또한 _파일 지점(file marks)_로 불림. 다른 지점으로의 이동은 아마 현재 버퍼를 다른 버퍼로 바꿀지 모른다. |
| `0` - `9` | viminfo | `0`은 viminfo파일이 마지막으로 쓰며진 지점이다. 실례로, 이것은 Vim이 마지막으로 프로세싱을 끝낸 지점을 의미한다. `1`은 Vim이 그 이전에 프로세싱을 끝냈던 지점이고, 그렇게 9번까지 있다. |

모션을 형성하기 위해 `'`/`g'`나 `` ` ``/`` g` ``을 지점 앞에 넣으세요. 

`mm`을 사용해서 지점 "m"에 현재 위치를 저장합니다. 그리고 파일의 다른 곳을 불러보다가
`'m` (빈 공간이 없는 첫문자) or `` `m `` (정확한 문자줄)로 이동해보세요. 만약 viminfo파일을
변경하면 소문자 지점들이 Vim을 종료한 후에서 저장되어 사용할 수 있습니다. `:h viminfo-'`를 보시죠.

`mM`을 사용해서 현재위치를 지점 `M`에 저장하세요. 다른 버퍼로 바꾼 후 `'M` or `` `M ``로 되돌아 와보세요.

다른 모션(motion)들:

| 모션(Motion)   | 이동(Jump to..) |
|------------------|-----------------|
| `'[`, `` `[ ``   | 첫 번째 줄이나 혹은 이전에 변경하거나 복사했던 문자로. |
| `']`, `` `] ``   | 마지막 줄이나 이전에 변경하거나 복사했던 문자로. |
| `'<`, `` `< ``   | 시작 줄이나 마지막으로 시각모드에서 선택핸던 문자로. |
| `'>`, `` `> ``   | 끝줄이나 마지막으로 시각모드에서 선택핸던 문자로. |
| `''`, ``` `` ``` | 마지막으로 점프하기 이전 위치로. |
| `'"`, `` `" ``   | 현재 버퍼의 마지막 종료시 위치로. |
| `'^`, `` `^ ``   | 마지막 삽입이 끝났던 위치로. |
| `'.`, `` `. ``   | 마지막 변경이 끝났던 위치로. |
| `'(`, `` `( ``   | 현재 문장의 시작점으로. |
| `')`, `` `) ``   | 현재 문장의 끝나는 점으로. |
| `'{`, `` `{ ``   | 현재 문단의 시작점으로. |
| `'}`, `` `} ``   | 현재 문단의 끝나는 점으로. |

지점들은 또한 [범위(range)](#ranges)와 같이 사용될 수 있습니다. 아마 봤을 수도 있을꺼에요.
궁금해 했을 수도 있을꺼구요: 시각모드로 어떤 텍스트를 선택한 후에 `:`을 누르세요.
이제 명령어 모드에 `:'<,'>`가 추가되었을 거에요. 이 의미는 이 뒤에 쓰여지는 명령은
시각모드에서 선택된 범위에 한해서만 명령이 실행된다는 뜻이에요.

`:marks`를 사용해서 모든 지점을 출력해보시죠. `:h mark-motions`에 있는 모든것을 읽어보세요.

## Completion

Vim은 여러가지의 자동완성들은 삽입모드에서 지원합니다. 만약에 여러개가 찾아지면,
팝업으로 선택을 가이드합니다.

전형적인 자동완성들로 태그, 모듈로서 삽인된 함수들이나 라이브러리들, 파일 이름들,
사전(dictionary)나 현재 버퍼에서 끌어온 간단한 단어가 있죠.

Vim은 각 자동완성을 위해 매핑을 제공하며, 모두 `<c-x>`로 시작합니다. (삽입모드로
사용해야 합니다.)

| 맵핑(Mapping) | 종류(Kind) | 도움(Help)         |
|---------|------|--------------|
| `<c-x><c-l>` | 줄 전체 | `:h i^x^l` |
| `<c-x><c-n>` | 현재 파일에서 키워드들| `:h i^x^n` |
| `<c-x><c-k>` | `'dictionary'` 옵션에서 키워드들| `:h i^x^k` |
| `<c-x><c-t>` | `'thesaurus'` 옵션에서 키워드들 | `:h i^x^t` |
| `<c-x><c-i>` | 현재 파일과 포함된 파일에서 키워드들| `:h i^x^i` |
| `<c-x><c-]>` | 태그| `:h i^x^]` |
| `<c-x><c-f>` | 파일이름 | `:h i^x^f` |
| `<c-x><c-d>` | 정의나 매크로| `:h i^x^d` |
| `<c-x><c-v>` | Vim 명령어| `:h i^x^v` |
| `<c-x><c-u>` | 사용자 지정 완성(`'completefunc'`에서 지정된) | `:h i^x^u` |
| `<c-x><c-o>` | 옴니(omni) 완성(`'omnifunc'`에서 지정된) | `:h i^x^o` |
| `<c-x>s`     | 스펠링 체크| `:h i^Xs` |

아마도 사용자 지정 완성과 옴니 완성에 혼동을 갖는 사람들도 있을거에요. 하지만,
그 둘은 기술적으로 같은 것이에요. 둘 다 현재 위치를 고려해서 단어목록을 반환하는
함수 하나를 갖습니다. 사용자 지정 완성은 개인적인 목적에 의해서 그들이 지정을 합니다.
아무거나 괜찮죠. 옴니 완성은 특정 파일 타입을 위해 만들며, class에서 struct와class
멤버 함수처럼 파일타일 플러그인에 의해 종종 지정됩니다.

Vim은 또한 `'complete'` 옵션을 이용하여 다양한 종류를 한 방에 완성시킬 수 있는 것도
허락합니다. 기본적으로 이 옵션이 꽤 많이 들어가 있으므로, 입맛에 맞게 바꾸세요. 
`<c-n>` (다음)이나 `<c-p>` (이전)를 이용해 이 완성들을 시작할 수 있습니다. 이 키들은
또한 팝업 메뉴에서 선택을 하는데도 쓰죠. 더 많은 정보는 `:h i^n`와 `:h 'complete'`를 보세요.

`:h 'completeopt'`를 확인해보는 것을 잊지 마세요. 팝업메뉴의 행동방식을 알려줍니다.
기본으로 들어간 셋팅도 괜찮지만, 저는 "noselect"옵션도 좋다고 봐요.

도움:

```
:h ins-completion
:h popupmenu-keys
:h new-omni-completion
```

## Motions, operators, text objects

**모션(움직임)**은 커서를 움직입니다.`h`/`j`/`k`/`l`는 모두 알죠. 혹은 `w`나 `b`도요. 게다가,
`/`도 모션이에요. 이것은 또한 숫자도 이용하죠. `2?the<cr>`는 끝에서 두번째로 일어난 "the"로 옮겨줍니다.

`:h navigation`를 한번 읽어보세요. 아래있는 모든 모션들에 관해 나와있습니다.

**연산자(오퍼레이터)**는 텍스트의 한 부분에 적용되요. 예를 들면, `d`, `~`, `gU`, `>` 같은 것들이죠.
이것들은 두 가지 모드에 사용되는데, 일반모드와 시각모드에요. 일반모드에서는, 연사자들이 먼저 모션보다
일찍 오죠, `>j`처럼요. 시각모드에서는, 연산자들이 단순하게 선택된 부분의 영역에만 적용된답니다.

모션처럼, 연산자도 숫자를 이용합니다. `2gUw`는 현재 단어와 다음단어를 대문자로
만듭니다. 모션과 연산자 모두 숫자를 받기 때문에, `2gU2w`도 역시 되고 이것은
`gU2w`를 두 번 실행하죠.

모든 연산자들을 `:h operator`으로 만나보세요. `:set tildeop`으로 `~`를 연산자로
활성화 시키세요.

**텍스트 객체**은 둘러싸인 부분에 적용되는데, 한방향으로만 작동하는 모션과는 반대죠.
전체 단어/전체 문장/괄호에 둘러싸인 모든 부분 등 실제로 객체들로 일을 한답니다.

텍스트 객체는 일반모드에서 커서를 움직이는데는 사용될 수 없어요. 왜냐면, 가장
뛰어난 커서들도 한 번에 두 방향으로 동시에 움직일 수 없기 때문이죠. 하지만 시각모드
는 괜찮죠. 왜냐면, 객체의 한 부분이 이미 선택되어 커서는 다른쪽으로 이동하기만 하면
되거든요.

텍스트 객체는 `i`나 (_안쪽_으로 생각) or `a` (_바깥둘레_로 생각)로 시작합니다.
`i`는 그 객체 자체에 영향을 주고, `a`는 그 객체와 따라오는 스페이스까지 포함하죠.
예를 들어 `diw`는 현재 단어를 지우고, `ci(`는 괄호 안의 모든 것을 지웁니다.

텍스트 객체도 숫자를 받죠. 커서가 `((( )))`의 가장 안쪽 혹은 그 중같에 있다고
상상해보세요. 그리고, `d2a(`를 쓰면, 2개의 괄호를 포함한 괄호 안쪽의 모든 것들을
함께 지울거에요.

모든 텍스트 객체를 보기위해 `:h text-objects`을 찾아보세요.

## Autocmds

Vim에서 일어나는 많은 이벤트 후에 한 동작을 실행시킬 수 있습니다. 가령, Vim이 시작하고
버퍼에 저장하죠. 이것들은 _자동명령어(autocmds)_라 합니다.

Vim은 자동명령어에 굉장히 의존하고 있어요. 믿지 못하겠나요? `:au`를 확인해보세요.
하지만 결과값에 놀라지 마세요. 이것들 모두가 이미 자동명령으로 실행 되고 있답니다.

모든 이벤트들을 보기 위해 `:h {event}`를 빠르게 한번 훑어보세요.
`:h autocmd-events-abc`도 찾아보세요.

전형적으로 사용하는 예시로 특정 파일에 적용하는 것을 볼 수 있죠.

```vim
autocmd FileType ruby setlocal shiftwidth=2 softtabstop=2 comments-=:#
```

어떻게 버퍼가 Ruby로 쓰여진지 알수 있을까요? 왜냐면, 다른 자동명령어가 이미
이것이 Ruby로 쓰여진것을 확인하고 다시 `FileType` 이벤트를 생성했기 때문이에요.

아마 모든 사람들이 그들의 vimrc 파일에 쓰는 것들 중 하나가 `filetype on`에요.
이것은 간단히 시작시점에 `filetype.vim`를 읽어서 모든 파일 타입에 관해 자동명령어를
지정하기 때문이죠.

자신있다면 한번 `:e $VIMRUNTIME/filetype.vim`을 보세요. "Ruby"를 한 번 찾아보시면,
그것이 단순하게 .rb 확장자로 되어었는 파일을 Ruby파일로 찾아내는 걸 발결할 수 있죠.

**알림**: 한 이벤트에 걸려있는 여러 자동명령어들은 생성된 순서되로 실행되게 되어 있죠.
`:au`이 이 순서를 알려 줍니다.

```vim
au BufNewFile,BufRead *.rb,*.rbw  setf ruby
```

`BufNewFile`과 `BufRead` 이벤트의 경우 Vim의 C코드에 하드코드 되어있고, 
`:e`나 비슷한 명령어를 통해서 열때마다 항상 이벤트가 생성됩니다. 그 다음,
`filetype.vim`에 있는 수백가지 파일 타입을 테스팅하는 거죠.

쉽게 말해, Vim은 이벤트와 자동명령어를 굉장히 많이 사용하며, 또한 꽤나 깔끔하게 
사용자 정의를 이벤트로 할 수 있는 인터페이스를 제공합니다.

도움: `:h autocommand`

## Changelist, jumplist

지난 100번의 변경사항들의 위치들이 **변경목록(changelist)**에 남겨둡니다. 같은
줄에서 일어난 몇 가지 작은 변경들은 합쳐져서 저장되고, 그렇지만 위치는 마지막 변경
을 한곳으로 저장이 되요(줄의 중같에 뭔가를 저장한 경우)

매번 커서를 이동할때마다, _이전_ 위치는 **이동목록(jumplist)**라는 곳에 저장이 됩니다.
이 목록은 100개를 저장 할 수 있으며, 각 윈도우는 이 목록은 하나씩 갖고 있죠.
한 개의 윈도우를 분할 하면, 이 목록은 복사되어 유지 됩니다.

이동(jump)은 이 명령어들 중 하나로 할 수 있죠.: `'`, `` ` ``, `G`, `/`, `?`, `n`, `N`,
`%`, `(`, `)`, `[[`, `]]`, `{`, `}`, `:s`, `:tag`, `L`, `M`, `H`, 그리고 새 파일을 시작하는
명령어들

| List       | List all entries | 이전에 저장했던 위치로 | 새로운 위치로 |
|------------|------------------|----------------------|----------------------|
| 이동목록(jumplist)   | `:jumps`         | `[count]<c-o>`       | `[count]<c-i>`       |
| 변경목록(changelist) | `:changes`       | `[count]g;`          | `[count]g,`          |

이 목록을 열어보면, `>` 표시가 현재 위치를 보여줄꺼게요. 보통,
포지션 1 아래 있고, 그곳이 가장 최근 위치를 나타내죠.

만약 이 목록을 Vim을 종료 한 후에서 유지하고 싶다면, viminfo파일을 사용해야 
할꺼에요. `:h viminfo-'`를 보세요.

**알림**: 마지막으로 이동했던 곳의 위치는 또한 [지점(mark)](#marks)에도 저장되고,
``` `` ```나 `''`으로 이동할 수 있죠.

도움:

```
:h changelist
:h jumplist
```

## Undo tree

마지막으로 변경한 텍스트의 상태도 저장됩니다. 변경을 되돌리기 위한 _undo_,
그리고 되돌린 변경을 다시 되돌리기 위한 _redo_를 사용할 수 있죠.

이것을 이해하는데가 중요한 것은 이것은 [queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))가
아니라 [tree](https://en.wikipedia.org/wiki/Tree_(data_structure))에 저장된다는 거에요!
당신의 만들 변경들은 트리의 노드들이고, 각각은 부모 노드를 갖고 있죠. 각 노드는
변경한 시간과 텍스트에 대한 정보를 들고 있답니다. 트리의 한 브랜치는 노드들로 엮여
부모를 통해 꼭대기로 올라갈 수 있죠. 새로운 가지는 undo를 한 후에 새로운 값을 넣으면
생성됩니다.
```
ifoo<esc>
obar<esc>
obaz<esc>
u
oquux<esc>
```

이제 당신은 3 줄이 있고, undo 트리는 이렇게 생겼죠.

```
     foo(1)
       /
    bar(2)
   /      \
baz(3)   quux(4)
```
undo 트리는 4개의 변경사항이 있습니다. 시간을 표시하는 숫자는 각 노드가 생성된
시간을 나타내요.

두 가지 방식으로 이 트리를 순회할 수 있는데, 하나는 _브랜치순(branch-wise)_이고,
다른 하나는 _시간순(time-wise)_입니다.

Undo (`u`)와 redo (`<c-r>`)는 브랜치 순으로 동작합니다. 이 명령어들은 현재 브랜치에서
위 아래로 움직이죠. `u`는 "bar"들 중 하나의 상태로 돌아갈꺼에요. `u`를 한 번 더
하게되면, 더 위로 올라가 "foo"에 도달하겠죠. 이제 `<c-r>`를 누르면 다시 "bar"로 
내려갈 꺼에요. 그리고 한 번 더 누르면 "quux"로 가겠죠. (이 브랜치 순 동작을 통해
"baz"로 갈 방법은 없습니다.)

반대로, `g-`와 `g+`는 시간순으로 작동합니다. 따라서, `u`가 한 것 처럼 `g-`는
"상태로 돌아가지 않습니다. 그렇지만 시간적으로 전에 있던 "baz"로 가죠. `g-`를
한 번 더 눌르면 이제 "bar"로 가는 방식이죠. 그래서, `g-`와 `g+`는 간단하게 시간
순으로 앞으로 뒤로 왔다 갔다 한답니다.

| 명령어 / 맵핑 | 동작 |
|-------------------|--------|
| `[count]u`, `:undo [count]` | Undo [count] 변경들. |
| `[count]<c-r>`, `:redo` | Redo [count] 변경들. |
| `U` | 가장 최근에 변경했던 줄에 일어난 모든 변경을 취소 합니다. |
| `[count]g-`, `:earlier [count]?` | 이전 텍스트 상태로 [count]번 이동합니다. "?"는  "s", "m", "h", "d", "f" 중 하나를 씁니다. `:earlier 2d`가 2일 전의 상태로 가는 것 처럼요. `:earlier 1f`는 마지막으로 파일을 저장했던 상태로 되돌아갑니다. |
| `[count]g+`, `:later [count]?` | 위와 같고, 반대방향으로 작동합니다. |

undo 트리는 메모리에 저장되고, Vim을 종료하면 없어집니다. 이것을 저장하기 위해서
[Undo files](#undo-files) 을 찾아보세요.

undo 트리에 여전히 혼란스럽다면, [undotree](https://github.com/mbbill/undotree)을 보세요.
이 트리 시각화를 완전 잘해 놨죠.

도움:

```
:h undo.txt
:h usr_32
```

## Quickfix and location lists

quickfix (빠른수정) 목록은 파일의 위치들을 저장하고 있습니다. 본질적으로, 이 목록은
파일 path, 줄 번호와 열(옵션), 그리고 설명을 갖고 있죠.

전형적인 예들로 컴파일러 에러를 만든다던가 혹은 grep의 결과들입니다.

Vim은 이 빠른수정 목록을 보여주기 위해 특별한 버퍼를 사용합니다. quickfix
버퍼죠. 이 버퍼의 각각의 줄은 이 목록의 한 아이템을 나타냅니다.

보통 이 목록을 보기위해 새로운 윈도우를 이용하죠. quickfix 윈도우라 합니다. 그러면,
마지막의 윈도우가 이 quickfix 윈도우와 연결이 됩니다.

quickfix 버퍼에서는 `<cr>`은 연결된 윈도우에 목록에서,
`<c-w><cr>`은 새로운 윈도우에서 선택한 항목을 엽니다.

이 quickfix 목록의 이름은 [Aztec C compiler](https://en.wikipedia.org/wiki/Aztec_C)에서 
"quick fix" 기능을 넣은데서 비롯되었죠. 

사실, quickfix 목록과 location(위치) 목록의 두 종류의 목록이 있습니다. 이 두 개는
거의 비슷하지만 아래에 차이점을 적어 두었습니다.

- 윈도우 하나당 단 하나의 quickfix 목록만 있지만, 여러개의 location 목록이 있을 수 있습니다.
- 그리고 약간 다른 명령어들로 사용합니다.

| 동작(Action)         | Quickfix     | Location     |
|----------------|--------------|--------------|
| 윈도우 열기 | `:copen`     | `:lopen`     |
| 윈도우 닫기 | `:cclose`    | `:lclose`    |
| 다음 항목 | `:cnext`     | `:lnext`     |
| 이전 항목 | `:cprevious` | `:lprevious` |
| 처음 항목 | `:cfirst`    | `:lfirst`    |
| 마지막 항목 | `:clast`     | `:llast`     |

Mind that the quickfix and location windows don't need to be open for these
commands to work.
이 명령어들을 사용하기 위해서 quickfix나 location 윈도우가 열려있을 필요는 
없습니다.

모든 명령어를 보거나 더 많은 정보는 `:h quickfix`에서 찾을 수 있습니다.

_quickfix_와 _location_은 때론 _qf_와 _loc_ 짧게 표현되기도 합니다.

**예제**:

우리의 오랜 친구인 `grep`으로 현재 폴더에서 특정 쿼리로 검색해서, 결과값을
quickfix에 넣어보죠.

```vim
:let &grepprg = 'grep -Rn $* .'
:grep! foo
<grep output - hit enter>
:copen
```
"foo"를 갖고 있는 어떤 파일들이 있다 가정하면, 이제 quickfix 윈도우에 나타날 것이에요.

## Macros

Vim은 [레지스터](#registers)에 쓰여진 문자들을 _녹화_할 수 있습니다. 이것은
어떤 일들을 자동화 시켜주는데 꽤나 좋은 방법이죠. (더 힘든일들은, Vim 스크립트로
대신할 수 있습니다.)

- `q`로 녹화를 시작하세요. (명령어 창에 "recording @q"라고 뜹니다.)
- `q`를 다시 누르면 녹화가 끝납니다.
- 이 매크로를 `[count]@q`로 실행하세요.
- `[count]@@`로 마지막 매크로를 다시 실행해보세요.

**예제 1:**

새로운 한 줄을 삽입하고, 10번 반복해보세요:

```
qq
iabc<cr><esc>
q
10@q
```

(같은 결과를 매크로 없이도 만들 수 있죠: `oabc<esc>10.`)

**예제 2:**

For adding line numbers in front of all lines, start on the first line and add
"1. " to it manually. Increment the number under the cursor by using `<c-a>`,
displayed as `^A`.
모든 줄 앞에 줄 번호를 넣기 위해서 첫 라인에 "1. "를 넣으세요. 커서에 있는 번호를
`^A`로 표시되는 `<c-a>`로 증가시켜 보세요. 

```
qq
0yf jP0^A
q
1000@q
```

이 예제에서 `1000@q`를 실행할 때, 우리는 사용하고 있는 파일이 1000줄이 넘지 않길 
바라죠. 하지만 _재귀적인 매크로_를 사용하면, 파일에 줄이 있을 동안만도 실행시킬 수 있죠.

```
qq
0yf jP0^A@q
q
@q
```

(물론 매크로 없이 가능합니다: `:%s/^/\=line('.') . '. '`)

제가 매크로를 사용하지 않고 같은 일을 수행 했지만, 이건 간단한 작업에 가능하죠.
더 복잡하고 멋진 자동화를 하려면, 매크로가 짱입니다.

이걸 보세요: [매크로 빠르게 변경하기](#quickly-edit-your-macros)

도움:

```
:h recording
:h 'lazyredraw'
```

## Colorschemes

색상정의(colorschemes)은 당신만의 Vim을 위해 스타일을 만들어 주는 방법이죠. Vim은 많은
컴포넌트들은 각기 모두 다른 색깔로 글자나 배경색 심지어 진하게 글자를 재정의 할 수 있습니다.

이렇게 정의가 가능하죠:
```vim
:highlight Normal ctermbg=1 guibg=red
```

이것은 편집기의 바탕화면 빨갛게 만들죠. 더 많은 정보를 위해 `:h :highlight`를 참조하세요.

이 색상정의는 `:highlight` 명령어들의 집합이죠.

실제로, 대부분의 색상정의들이 두 개로 정의되어 있죠. 위에 있는 예제는 `ctermbg`나 `guibg`를
통해서 색깔을 지정합니다. 이전 정의(`cterm*`)는 Vim이 터미널에서 시작했을때만 쓰여지죠. 예를 들어
xterm같은 것이요. 후자(`gui*`)는 gvim이나 macVim과 같은 그래픽 환경에서 사용됩니다.

Vim 터미널에서 색상정의를 사용하게 되고, 색깔이 스크린샷에 나와있는 것처럼 나오지 않으면,
아마도 색상정의가 GUI를 위해서만으로 정의 되어 있을 수 있습니다. 반대로, 그래픽 환경에서
Vim을 사용하는데 색깔이 약간 다르다고 느껴진다면, 색상정의가 터미널만 정의 되어 있을 수 있죠.

후자의 경우는 NeoVim이나 Vim 7.4.1830 이후 버젼에서 트루 컬러를 활성화시켜 문제해결이
가능하죠. 이렇게 하면 Vim은 GUI에 정의된 것을 사용합니다. 하지만 터미널이나 다른 그 사이의
다른 소프트웨어(예: tmux)도 트루컬러를 다룰 수 있는 능력이 생기죠. ([이
gist](https://gist.github.com/XVilka/8346728)에 소개글이 잘 나와있죠)

도움:

- `:h 'termguicolors'`
- [색상정의 목록](PLUGINS.md#colorschemes-1)
- [색상정의 겉핣기](#cosmetic-changes-to-colorschemes)

## Folding

어떤 텍스트(혹은 소스코드)던지 특정 구조를 갖고 있죠. 구조를 갖고 있다는 말은,
논리적으로 구분된 텍스트의 지역들이 있다는 말이죠. 접기(Folding)는 그런 지역들을 한 줄로
접고, 짧게 줄임말로 표시해 줍니다. 많은 명령어들이 이 _접힌줄(folds)_의 지역에서
동작하죠. 접힌줄은 또한 접힌줄을 포함할 수 있습니다.

Vim은 몇 가지 접는 방법들의 종류를 구분합니다. 


| 접는방법('foldmethod') | 사용법 |
|--------------|-------|
| diff         | diff 윈도우에서 변하지 않은 텍스트를 접을 때 사용됨. |
| expr         | `'foldexpr'`를 사용하여 새로운 접는 방법을 생성. |
| indent       | 들임쓰기에 따라 접기. |
| manual       | `zf`, `zF`, `:fold`로 손수 접기. |
| marker       | 텍스트에 있는 특정 지시자를 따라 접기(보통 주석). |
| syntax       | 문법에 따른 접기, 예) `if` 블럭. |

**알림**: 접기는 꽤나 비싼 작업일 수 있죠. 따라서, 성능이 저하되는 경험(글을 쓸 때
작은 지연)이 생기면, [FastFold](https://github.com/Konfekt/FastFold)를 한 번 보세요.
이것은 Vim으 접힌줄을 필요하지 않은데 업데이트 하는 것을 방지합니다.

도움:

```
:h usr_28
:h folds
```

## Sessions

만약 저장된 **뷰(view)**(`:h :mkview`)가 있으면, 현재 윈도우의 상태(옵션들과 맵핑들)을 
다음에 또 사용하게 위해서 저장(`:h :loadview`)할 수 있습니다.

하나의 **세션(session)**은 모든 윈도우들의 뷰들과 글로벌 세팅을 저장하죠. 다시 말해,
현재 Vim 인스터스의 스냅샷을 만들어서, 세션파일로 저장해 두는 것입니다.
강조 할께요. 이것은 현재 상태를 저장합니다; 세션을 저장한 뒤에 일어나는 것들은
세션파일로 같이 들어가지 않습니다. 세션 파일을 다시 업데이트 하려면, 다시 저장하면 됩니다.

이것은 당신의 _프로젝트들_을 저장하기 위해 완벽한 방법이죠. 프로젝트들 사이를 옮기기도 쉽죠.

바로 시도해 보세요. 몇 개의 윈도우와 탭을 열고, `:mksession Foo.vim`를 넣어 보세요.
만약 파일 이름을 빼먹으면 `Session.vim`으로 생성될 꺼에요. 이 파일은 현재 디렉토리에
저장될 것이고, `:pwd`를 확인해보세요. Vim을 재시작하고 `:source Foo.vim`을 해보세요. 
짜잔!. 버퍼목록, 윈도우 상태, 맵핑, 현재 디렉토리등 모든 것이 세션을 저장하기 이전과
같죠. 좀 더 가지고 놀다가 기존의 세션 파일을 `:mksession! Foo.vim`으로 덮어씌워 보세요.

하나의 세션 파일은 단지 Vim 인스턴스의 특정 상태를 복구하기 위한 Vim명령어 들의 집합이죠. 
그러니 `:vs Foo.vim`로 한 번 들여다 보세요.

또한 `'sessionoptions'`을 지정함으로써, Vim이 무엇을 정장해야할지 지정할 수 있습니다.

스크립팅을 위해서, Vim은 내부 변수 `v:this_session`에 마지막으로 쓰여졌거나 로드된 세션의
이름을 저장합니다.

도움:

```
:h Session
:h 'sessionoptions'
:h v:this_session
```

## Locality

Many of the concepts mentioned above also have _local_ counterparts:

| Global | Local | Scope | Help |
|--------|-------|-------|------|
| `:set`     | `:setlocal`           | buffer or window | `:h local-options`    |
| `:map`     | `:map <buffer>`       | buffer           | `:h :map-local`       |
| `:autocmd` | `:autocmd * <buffer>` | buffer           | `:h autocmd-buflocal` |
| `:cd`      | `:lcd`                | window           | `:h :lcd`             |
| `<leader>` | `<localleader>`       | buffer           | `:h maplocalleader`   |

[Variables also have different scopes](https://vimhelp.appspot.com/usr_41.txt.html#41.2).

# Usage

## Getting help offline

Vim comes with great documentation in the form of single text files with a
special layout. Vim uses a system based on tags for accessing certain parts of
those help files.

First of all, read this: `:help :help`. This will open the file
`$VIMRUNTIME/doc/helphelp.txt` in a new window and jump to the `:help` tag
within that file.

A few simple rules:

- options are enclosed in single quotes, e.g. `:h 'textwidth'`
- VimL functions end in `()`, e.g. `:h reverse()`
- commands start with `:`, e.g. `:h :echo`

You can use `<c-d>` (this is <kbd>ctrl</kbd>+<kbd>d</kbd>) to list all tags that
match the currently entered query. E.g. `:h tab<c-d>` will get you a list of all
tags from `tab` over `'softtabstop'` to `setting-guitablabel`.

You want to list all VimL functions? Simple: `:h ()<c-d>`. You want to list all
VimL functions that concern windows? `:h win*()<c-d>`.

This quickly becomes second nature, but especially in the beginning, you
sometimes don't know any part of the tag you are looking for. You can only
imagine some keywords that could be involved. `:helpgrep` to the rescue!

```
:helpgrep backwards
```

This will look for "backwards" in all documentation files and jump to the first
match. The matches will be assembled in the quickfix list. Use `:cn`/`:cp` to
jump to the next/previous match. Or use `:copen` to open the quickfix window,
navigate to an entry and hit `<cr>` to jump to that match. See `:h quickfix` for
the whole truth.

## Getting help offline (alternative)

This list was compiled by @chrisbra, one of the most active Vim developers, and
posted to [vim_dev](https://groups.google.com/forum/#!forum/vim_dev).

It's reposted here with minor changes.

---

If you know what you are looking for, it is usually easier to search for it
using the help system, because the subjects follow a certain style guide.

Also, the help has the advantage of belonging to your particular Vim version, so
that obsolete topics or topics that have been added later won't turn up.

Therefore, it is essential to learn the help system and the language it uses.
Here are some examples (not necessarily complete and I might have forgotten
something).

1. Options are enclosed in single quotes. So you would use `:h 'list'` to go to
   the help topic for the list option. If you only know, you are looking for a
   certain option, you can also do `:h options.txt` to open the help page which
   describes all option handling and then you can search using regular
   expressions e.g. `/width`. Certain options have their own namespace, e.g. `:h
   cpo-a`, `:h cpo-A`, `:h cpo-b`, and so on.

2. Normal mode commands are just that. Use `:h gt` to go to the help page for
   the "gt" command.

3. Regexp items always start with "/", so `:h /\+` takes you to the help item
   for the "\+" quantifier in Vim regexes. If you need to know anything about
   regular expressions, start reading at `:h pattern.txt`.

4. Key combinations. They usually start with a single letter indicating the mode
   for which they can be used. E.g. `:h i_CTRL-X` takes you to the family of
   CTRL-X commands for insert mode which can be used to auto complete different
   things. Note that certain keys will always be written the same, e.g. Control
   will always be CTRL. Note, for normal mode commands, the "n" is left away,
   e.g. `:h CTRL-A`. In contrast, `:h c_CTRL-R` will describe what CTRL-R does
   when entering commands in the command line and `:h v_Ctrl-A` talks about
   incrementing numbers in visual mode and `:h g_CTRL-A` talks about the g<C-A>
   command (thus you have to press "g" then <Ctrl-A>). Here the "g" stand for
   the normal command "g" which always expect a second key before doing
   something similar to the commands starting with "z".

5. Registers always start with "quote" so use `:h quote` to find out about the
   special ":" register.

6. Vim script (VimL) is available at `:h eval.txt`. Certain aspects of the
   language are available at `:h expr-X` where 'X' is a single letter, e.g. `:h
   expr-!` will take you to the topic describing the '!' (Not) operator for
   VimL. Also important, see `:h function-list` to find a short description of
   all functions available.

7. Mappings are talked about in the help page `:h map.txt`. Use `:h mapmode-i`
   to find out about the `:imap` command. Also use `:map-topic` to find out
   about certain subtopics particular for mappings (e.g. `:h :map-local` for
   buffer-local mappings or `:h map_bar` for how the '|' is handled in mappings.

8. Command definitions are talked about at `:h command-*`, so use :h command-bar
   to find out about the '!' argument for custom commands.

9. Window management commands always start with CTRL-W, so you find the
   corresponding help at `:h CTRL-W_*` (e.g. `:h CTRL-W_p` for switch to the
   previously accessed window). You can also access `:h windows.txt` and read
   your way through, if you are looking for window handling command.

10. Ex commands always start with ":", so `:h :s` covers the ":s" command.

11. Use CTRL-D after typing a topic and let Vim try to complete to all available
    topics.

12. Use `:helpgrep` to search in all help pages (usually also includes help
    pages by installed plugins). See `:h :helpgrep` for how to use it. Once you
    have searched for a topic, all matches are available in the quickfix (or
    location) window which can be opened with `:copen` or `:lopen`. There you
    can also use `/` to further filter the matches.

13. `:h helphelp` contains some information on how to use the help.

14. The user manual. This describes help topics for beginners in a rather
    friendly way. Start at `:h usr_toc.txt` to find the table of content (as you
    might have guessed). Skimming over that help to find certain topics, .e.g
    you will find an entry "Digraphs" and "Entering special characters" in
    chapter 24 (so use `:h usr_24.txt` to go to that particular help page).

15. Highlighting groups always start with `hl-*`. E.g. `:h hl-WarningMsg` talks
    about the "WarningMsg" highlighting group.

16. Syntax highlighting is namespaced to ":syn-topic", e.g. `:h :syn-conceal`
    talks about the conceal argument for the :syn command.

17. Quickfix commands usually start with ":c", while location list commands
    usually start with ":l".

18. `:h BufWinLeave` talks about the BufWinLeave autocmd. Also, `:h
    autocommands-events` talks about all possible events.

19. Startup arguments always start with "-", so `:h -f` takes you to the help of
    the "-f" command switch of Vim.

20. Compiled extra features always start with "+", so `:h +conceal` talks about
    the conceal support.

21. Error codes can be looked up directly in the help. `:h E297` takes you
    exactly to the description of the error message. Sometimes however, those
    error codes are not described, but rather are listed at the Vim command that
    usually causes this. E.g. `:h hE128` takes you directly to the `:function`
    command.

22. Documentation for included syntax files is usually available at `:h
    ft-*-syntax`. E.g. `:h ft-c-syntax` talks about the C syntax file and the
    options it provides. Sometimes, additional sections for omni completion (`:h
    ft-php-omni`) or filetype plugins (`:h ft-tex-plugin`) are available.

Also, a link to the user documentation (which describes certain commands more
from a user perspective and less detailed) will be mentioned at the top of help
pages if they are available. So `:h pattern.txt` mentions the user guide topics
`:h 03.9` and `:h usr_27`.

## Getting help online

If you have an issue you can't resolve or are in need of general guidance, see
the [vim_use](https://groups.google.com/forum/#!forum/vim_use) mailing list.
Another great resource is using
[IRC](https://de.wikipedia.org/wiki/Internet_Relay_Chat). The channel `#vim` on
[Freenode](https://freenode.net) is huge and usually full of helpful people.

If you want to report a Vim bug, use the
[vim_dev](https://groups.google.com/forum/#!forum/vim_dev) mailing list.

## Autocmds in practice

You can trigger any event right now: `:doautocmd BufRead`.

### User events

Especially for plugins it's useful to create your own "User" events:

```vim
function! Chibby()
  " A lot of stuff is happening here.
  " And at last..
  doautocmd User ChibbyExit
endfunction
```

Now users of your plugin can execute anything when Chibby finishes running:

```vim
autocmd User ChibbyExit call ChibbyCleanup()
```

By the way, if there's no "catching" :autocmd, :doautocmd will output a pesky
"No matching autocommands" message. That's why many plugins use `silent
doautocmd ...` instead. But this has the disadvantage, that you can't simply use
`echo "foo"` in the :autocmd, you have to use `unsilent echo "foo"` instead..

That's why it's better to check if there even is a receiving autocmd and not
bothering emitting the event otherwise:

```vim
if exists('#User#ChibbyExit')
  doautocmd User ChibbyExit
endif
```

Help: `:h User`

### Nested autocmds

By default, autocmds do not nest! If an autocmd executes a command, which in
turn would usually trigger another event, it won't happen.

Let's say every time you start Vim, you want to automatically open your vimrc:

```vim
autocmd VimEnter * edit $MYVIMRC
```

When you now start Vim, it will open your vimrc, but the first thing you'll
notice is that there won't be any highlighting although usually there would be.

The problem is that `:edit` in your non-nested autocmd won't trigger the
"BufRead" event, so the filetype never gets set to "vim" and
`$VIMRUNTIME/syntax/vim.vim` never sourced. See `:au BufRead *.vim`. Use this
instead:

```vim
autocmd VimEnter * nested edit $MYVIMRC
```

Help: `:h autocmd-nested`

## Clipboard

Required [features](#what-kind-of-vim-am-i-running): `+clipboard` and optionally
`+xterm_clipboard` if you want to use the `'clipboard'` option on a Unix system
with a Vim that doesn't have GUI support.

Help:

```
:h 'clipboard'
:h gui-clipboard
:h gui-selections
```

Also see: [Bracketed paste (or why do I have to set 'paste' all the
time?)](#bracketed-paste-or-why-do-i-have-to-set-paste-all-the-time)

### Clipboard usage (Windows, macOS)

Windows comes with a
[clipboard](https://msdn.microsoft.com/en-us/library/windows/desktop/ms649012(v=vs.85).aspx)
and macOS comes with a
[pasteboard](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PasteboardGuide106/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008100-SW1).

Both work like most users would expect them to work. You copy selected text with
`ctrl+c`/`cmd+c` and paste them in another application with `ctrl+v`/`cmd+v`.

Note that copied text is actually transferred to the clipboard, so you can close
the application you copied from before pasting in another application without
problems.

Whenever this happens, the clipboard register `*` gets filled with the
selection. From Vim use `"*y` and `"*p` to yank and paste from the clipboard
respectively.

If you don't even want to specify the `*` register all the time, put this in
your vimrc:

```vim
set clipboard=unnamed
```

Usually all yank/delete/put operations fill the `"` register, now the `*`
register is used for the same operations, therefore simply `y` and `p` will be
enough.

Let me repeat: Using the option above means that every yank/paste, even when
only used in the same Vim window, will alter the clipboard. Decide for yourself
if this is useful or not.

If you're even too lazy to type `y`, you can send every visual selection to the
clipboard by using these settings:

```vim
set clipboard=unnamed,autoselect
set guioptions+=a
```

Help:

```
:h clipboard-unnamed
:h autoselect
:h 'go_a'
```

### Clipboard usage (Linux, BSD, ...)

If your OS uses [X](http://www.x.org/wiki), things work a bit different. X
implements the [X Window System
Protocol](http://www.x.org/releases/X11R7.7/doc/xproto/x11protocol.html) which
happens to be at major version 11 since 1987, hence X is also often called X11.

Prior, in X10, [cut
buffers](http://www.x.org/releases/X11R7.7/doc/xorg-docs/icccm/icccm.html#Peer_to_Peer_Communication_by_Means_of_Cut_Buffers)
were introduced that kind of worked like a _clipboard_ as in copied text was
actually held by X and it was accessible by all other applications. This
mechanism still exists in X, but its use is deprecated now and most software
doesn't use it anymore.

Nowadays data is transferred between applications by the means of
[selections](http://www.x.org/releases/X11R7.7/doc/xorg-docs/icccm/icccm.html#Peer_to_Peer_Communication_by_Means_of_Selections).
From the 3 _selection atoms_ defined, only 2 are used in practice: PRIMARY and
CLIPBOARD.

Selections work roughly like this:

```
Program A: <ctrl+c>
Program A: assert ownership of CLIPBOARD
Program B: <ctrl+v>
Program B: note that ownership of CLIPBOARD is hold by Program A
Program B: request data from Program A
Program A: respond to request and send data to Program B
Program B: receives data from Program A and inserts it into the window
```

| Selection | When used? | How to paste? | How to access from Vim? |
|-----------|------------|---------------|-------------------------|
| PRIMARY   | Selecting text              | `middle-click`, `shift+insert` | `*` register |
| CLIPBOARD | Selecting text and `ctrl+c` | `ctrl+v`                       | `+` register |

**NOTE**: Selections (no, not even the CLIPBOARD selection) are never kept in
the X server! Thus, you lose the data copied with `ctrl+c` when the application
closes.

Use `"*p` to paste the PRIMARY selection or `"+y1G` to yank the entire file to
the CLIPBOARD selection.

If you happen to access one of the two registers all the time, consider using:

```vim
set clipboard^=unnamed      " * register
" or
set clipboard^=unnamedplus  " + register
```

(The `^=` is used to prepend to the default value, `:h :set^=`.)

This will make all yank/delete/put operations use either `*` or `+` instead of
the unnamed register `"`. Afterwards you can simply use `y` or `p` for accessing
your chosen X selection.

Help:

```vim
:h clipboard-unnamed
:h clipboard-unnamedplus
```

## Restore cursor position when opening file

When you open a file, the cursor will be positioned at line 1, column 1.
Fortunately the viminfo file remembers [marks](#marks). The `"` mark contains
the position in the buffer where you left off.

```vim
autocmd BufReadPost *
    \ if line("'\"") > 1 && line("'\"") <= line("$") |
    \   execute "normal! g`\"" |
    \ endif
```

Read: If the mark `"` contains a line number greater than line 1 but not greater
than the last line in the file, jump to it.

    :h viminfo-'
    :h `quote
    :h g`

## Temporary files

### Backup files

Before saving a file, Vim creates a backup file. If writing to disk was
successful, the backup file will be deleted.

With `:set backup`, the backup will persist. This means, the backup file will
always have the same content as the original file _before_ the most recent save.
It's up to you to decide whether this is useful or not.

You can disable backups entirely with `:set nobackup nowritebackup`, but you
shouldn't need to nowadays. `'writebackup'` is a security feature that makes
sure that you don't lose the original file in case saving it should ever fail,
no matter whether you keep the backup file afterwards or not.

If you frequently use Vim to edit huge files, [and you probably
shouldn't](#editing-huge-files-is-slow), you can exclude those from backups with
`'backupskip'`.

Vim knows different ways to create a backup: _copying_ and _renaming_.

- **Copying**
    1. A full copy of the original file is created and used as backup.
    1. The original file gets emptied and then filled with the content of the
    Vim buffer.
- **Renaming**
    1. The original file is renamed to the backup file.
    1. The content of the Vim buffer gets written to a new file with the name of
    the original file.

See `:h 'backupcopy'` for all the nitty-gritty details.

---

Demo:

```vim
:set backup backupskip= backupdir=. backupext=-backup
:e /tmp/foo
ifoo<esc>
:w
" original file gets created, no need for backup file
obar<esc>
:w
" backup file is created, original file gets updated
```

```diff
$ diff -u /tmp/foo-backup /tmp/foo
--- /tmp/foo-backup     2017-04-22 15:05:13.000000000 +0200
+++ /tmp/foo    2017-04-22 15:05:25.000000000 +0200
@@ -1 +1,2 @@
 foo
+bar
```

---

    :h backup
    :h write-fail

### Swap files

When editing a file, unsaved changes get written to a swap file.

Get the name of the current swap file with `:swapname`. Disable them with `:set
noswapfile`.

A swap file gets updated either all 200 characters or when nothing was typed for
4 seconds. They get deleted when you stop editing the file. You can change these
numbers with `:h 'updatecount'` and `:h 'updatetime'`.

If Vim gets killed (e.g. power outage), you lose all changes since the last time
the file was written to disk, but the swap file won't be deleted. Now, if you
edit the file again, Vim will offer the chance to recover the file from the swap
file.

When two people try to edit the same file, the second person will get a notice
that the swap file already exists. It prevents people from trying to save
different versions of a file. If you don't want that behaviour, see `:h
'directory'`.

    :h swap-file
    :h usr_11

### Undo files

The [undo tree](#undo-tree) is kept in memory and will be lost when Vim quits.
If you want it to persist, `:set undofile`. This will save the undo file for
`~/foo.c` in `~/foo.c.un~`.

    :h 'undofile'
    :h undo-persistence

### Viminfo files

When backup, swap, and undo files are all about text state, viminfo files are
used for saving everything else that would otherwise be lost when quitting Vim.
The viminfo file keeps histories (command line, search, input), registers,
marks, buffer list, global variables etc.

By default, the viminfo is written to `~/.viminfo`.

    :h viminfo
    :h 'viminfo'

### Example configuration for temporary files

Put all temporary files in their own directory under `~/.vim/files`:

```vim
" create directory if needed
if !isdirectory($HOME.'/.vim/files') && exists('*mkdir')
  call mkdir($HOME.'/.vim/files')
endif

" backup files
set backup
set backupdir   =$HOME/.vim/files/backup/
set backupext   =-vimbackup
set backupskip  =
" swap files
set directory   =$HOME/.vim/files/swap//
set updatecount =100
" undo files
set undofile
set undodir     =$HOME/.vim/files/undo/
" viminfo files
set viminfo     ='100,n$HOME/.vim/files/info/viminfo
```

## Editing remote files

Vim comes with the netrw plugin that enables editing remote files. Actually it
transfers the remote file to a local temporary file via scp, opens a buffer
using that file, and writes the changes back to the remote file on saving.

This is extremely useful if you want to use your local configuration opposed to
ssh'ing into a server and use whatever the admins want you to use.

```
:e scp://bram@awesome.site.com/.vimrc
```

If you have a `~/.ssh/config` set up already, this gets used automatically:

```
Host awesome
    HostName awesome.site.com
    Port 1234
    User bram
```

Assuming the above content in `~/.ssh/config`, this works just as well:

```
:e scp://awesome/.vimrc
```

Similar can be done with a `~/.netrc`, see `:h netrw-netrc`.

Make sure to read `:h netrw-ssh-hack` and `:h g:netrw_ssh_cmd`.

---

Another possibility is using [sshfs](https://wiki.archlinux.org/index.php/Sshfs)
which uses [FUSE](https://en.wikipedia.org/wiki/Filesystem_in_Userspace) to
mount a remote filesystem into your local filesystem.

## Managing plugins

[Pathogen](https://github.com/tpope/vim-pathogen) was the first popular tool for
managing plugins. Actually it just adjusts the _runtimepath_ (`:h 'rtp'`) to
include all the things put under a certain directory. You have to clone the
repositories of the plugins there yourself.

Real plugin managers expose commands that help you to install and update plugins
from within Vim.

[List of plugin managers](PLUGINS.md#plugin-managers)

## Block insert

This is a technique to insert the same text on multiple consecutive lines at the
same time. See this
[demo](https://raw.githubusercontent.com/mhinz/vim-galore/master/static/images/content-block_insert.gif).

Switch to visual block mode with `<c-v>`. Afterwards go down for a few lines.
Hit `I` or `A` and start entering your text.

It might be a bit confusing at first, but text is always entered for the current
line and only after finishing the current insertion, the same text will be
applied to all other lines of the prior visual selection.

So a simple example is `<c-v>3jItext<esc>`.

If you have lines of different length and want to append the same text right
after the end of each line, do this: `<c-v>3j$Atext<esc>`.

Sometime you need to place the cursor somewhere after the end of the current
line. You can't do that by default, but you can set the `virtualedit` option:

```vim
set virtualedit=all
```

Afterwards `$10l` or `90|` work even after the end of the line.

See `:h blockwise-examples` for more info. It might seem complicated at first,
but quickly becomes second nature.

If you want to get real fancy, have a look at
[multiple-cursors](https://github.com/terryma/vim-multiple-cursors).

## Running external programs and using filters

Disclaimer: Vim is single-threaded, so running an external program in the
foreground will block everything else. Sure, you can use one of Vim's
programming interfaces, e.g. Lua, and use its thread support, but during that
time the Vim process is blocked nevertheless. Neovim fixed that by adding a
proper job API.

(Apparently Bram is thinking about adding job control to Vim as well. If you
have a very recent version, see `:helpgrep startjob`.)

Use `:!` to start a job. If you want to list the files in the current working
directory, use `:!ls`. Use `|` for piping in the shell as usual, e.g. `:!ls -1 |
sort | tail -n5`.

Without a range, the output of `:!` will be shown in a scrollable window. On the
other hand, if a range is given, these lines will be
[filtered](https://en.wikipedia.org/wiki/Filter_(software)). This means they
will be piped to the
[stdin](https://en.wikipedia.org/wiki/Standard_streams#Standard_input_.28stdin.29)
of the filter program and after processing be replaced by the
[stdout](https://en.wikipedia.org/wiki/Standard_streams#Standard_output_.28stdout.29)
of the filter. E.g. for prepending numbers to the next 5 lines, use this:

    :.,+4!nl -ba -w1 -s' '

Since manually adding the range is quite burdensome, Vim also provides some
helpers for convenience. As always with ranges, you can also select lines in
visual mode and then hit `:`. There's also an operator `!` that takes a motion.
E.g. `!ip!sort` will sort the lines of the current paragraph.

A good use case for filtering is the [Go programming
language](https://golang.org). The indentation is pretty opinionated, it even
comes with a filter called `gofmt` for indenting Go source code properly. So
plugins for Go often provide helper commands called `:Fmt` that basically do
`:%!gofmt`, so they indent all lines in the file.

People often use `:r !prog` to put the output of prog below the current line,
which is fine for scripts, but when doing it on the fly, I find it easier to use
`!!ls` instead, which replaces the current line.

    :h filter
    :h :read!

## Cscope

[Cscope](http://cscope.sourceforge.net/) does more things than
[ctags](http://ctags.sourceforge.net/), but only supports C (and C++ and Java to
some extent).

Whereas a tags file only knows where a symbol was defined, a cscope database
knows much more about your data:

- Where is this symbol defined?
- Where is this symbol used?
- What is this global symbol's definition?
- Where did this variable get its value?
- Where is this function in the source files?
- What functions call this function?
- What functions are called by this function?
- Where does the message "out of space" come from?
- Where is this source file in the directory structure?
- What files include this header file?

### 1. Build the database

Do this in the root of your project:

```sh
$ cscope -bqR
```

This will create 3 files: `cscope{,.in,.po}.out` in the current working
directory. Think of them as your database.

Unfortunately `cscope` only analyzes `*.[c|h|y|l]` files by default. If you want
to use cscope for a Java project instead, do this:

```sh
$ find . -name "*.java" > cscope.files
$ cscope -bq
```

### 2. Add the database

Open a connection to your freshly built database:

```vim
:cs add cscope.out
```

Verify that the connection was made:

```vim
:cs show
```

(Yes, you can add multiple connections.)

### 3. Query the database

```vim
:cs find <kind> <query>
```

E.g. `:cs find d foo` will list all functions that are called by `foo(...)`.

| Kind | Explanation |
|------|-------------|
| s    | **s**ymbol: find all references to the token        |
| g    | **g**lobal: find global definition(s) of the token  |
| c    | **c**alls: find all calls to the function           |
| t    | **t**ext: find all instances of the text            |
| e    | **e**grep: egrep search for the word                |
| f    | **f**ile: open the filename                         |
| i    | **i**ncludes: find files that include the filename  |
| d    | **d**epends: find functions called by this function |

I suggest some convenience mappings e.g.:

```vim
nnoremap <buffer> <leader>cs :cscope find s  <c-r>=expand('<cword>')<cr><cr>
nnoremap <buffer> <leader>cg :cscope find g  <c-r>=expand('<cword>')<cr><cr>
nnoremap <buffer> <leader>cc :cscope find c  <c-r>=expand('<cword>')<cr><cr>
nnoremap <buffer> <leader>ct :cscope find t  <c-r>=expand('<cword>')<cr><cr>
nnoremap <buffer> <leader>ce :cscope find e  <c-r>=expand('<cword>')<cr><cr>
nnoremap <buffer> <leader>cf :cscope find f  <c-r>=expand('<cfile>')<cr><cr>
nnoremap <buffer> <leader>ci :cscope find i ^<c-r>=expand('<cfile>')<cr>$<cr>
nnoremap <buffer> <leader>cd :cscope find d  <c-r>=expand('<cword>')<cr><cr>
```

So, when `:tag` (or `<c-]>`) jumps to a definition from the tags file, `:cstag`
does the same, but also takes connected cscope databases into account. The
option `'cscopetag'` makes `:tag` act like `:cstag` automatically. This is very
convenient if you already have tag-related mappings.

Help: `:h cscope`

## MatchIt

Since Vim is written in C, a lot of features assume C-like syntax. By default,
if your cursor is on `{` or `#endif`, you can use `%` to jump to the
corresponding `}` or `#ifdef` respectively.

Vim comes bundled with a plugin called matchit.vim which is not enabled by
default. It makes `%` also cycle through HTML tags, if/else/endif constructs in
VimL etc. and introduces a few new commands.

#### Installation for Vim 8

```vim
" vimrc
packadd! matchit
```

#### Installation for Vim 7 and older

```vim
" vimrc
runtime macros/matchit.vim
```

Since the documentation of matchit is pretty extensive, I suggest also doing the
following once:

```vim
:!mkdir -p ~/.vim/doc
:!cp $VIMRUNTIME/macros/matchit.txt ~/.vim/doc
:helptags ~/.vim/doc
```

#### Small intro

The plugin is ready to use now. See `:h matchit-intro` for the supported
commands and `:h matchit-languages` for the supported languages.

That said, it's easy to define your own matching pairs:

```vim
autocmd FileType python let b:match_words = '\<if\>:\<elif\>:\<else\>'
```

Afterwards you can cycle through these 3 statements in any Python file by using
`%` (forward) or `g%` (backward).

Help:

```
:h matchit-install
:h matchit
:h b:match_words
```

## True colors

Using true colors in a terminal emulator means being able to use 24 bits for RGB
colors. That makes 16777216 (2^24) colors instead of the usual 256.

As explained [here](#colorschemes), colorschemes can actually be _two_
colorschemes by having definitions for terminals (xterm) and for GUIs (gvim).
This made sense before terminal emulators learned about true colors.

After `:set termguicolors`, Vim starts emitting escape sequences only understood
by a terminal emulator that supports true colors. When your colors look weird,
chances are your terminal emulator doesn't support true colors or your
colorcheme has no GUI colors defined.

Many people use the terminal multiplexer
[tmux](https://github.com/tmux/tmux/wiki) which basically sits in between the
terminal emulator and Vim. To make tmux _forward_ the true color escape
sequences emitted by Vim, you have to put the following in the user's
`.tmux.conf`:

```
set-option -g  default-terminal 'tmux-256color'
set-option -ga terminal-overrides ',xterm-256color:Tc'
```

- The first line should be the same for most people and denotes the `$TERM` to
  be used _within_ tmux.
- The second line adds the tmux-specific `Tc` (true color) capability to the
  other terminfo entries of `xterm-256color`. Obviously this assumes that the
  user is using `TERM=xterm-256color` _outside_ of tmux.

So, here is the checklist for enabling true colors:

- Read `:h 'termguicolors'`.
- Put `set termguicolors` in your vimrc.
- Make sure your colorscheme has color definitions for GUIs. (It should contain
  lines with `guifg` and `guibg`.)
- Make sure your terminal emulator of choice supports true colors.
- Using tmux? Configure it to add the `Tc` capability.

A popular reference for colors in the terminal:
https://gist.github.com/XVilka/8346728

# Tips

## Go to other end of selected text

`o` and `O` in a visual selection make the cursor go to the other end. Try with
blockwise selection to see the difference. This is useful for quickly changing
the size of the selected text.

```
:h v_o
:h v_O
```

## Saner behavior of n and N

The direction of `n` and `N` depends on whether `/` or `?` was used for
searching forward or backward respectively. This is pretty confusing to me.

If you want `n` to always search forward and `N` backward, use this:

```vim
nnoremap <expr> n  'Nn'[v:searchforward]
xnoremap <expr> n  'Nn'[v:searchforward]
onoremap <expr> n  'Nn'[v:searchforward]

nnoremap <expr> N  'nN'[v:searchforward]
xnoremap <expr> N  'nN'[v:searchforward]
onoremap <expr> N  'nN'[v:searchforward]
```

## Saner command-line history

If you're anything like me, you're used to going to next and previous items via
`<c-n>` and `<c-p>` respectively. By default, this also works in the
command-line and recalls older or more recent command-lines from history.

So far, so good. But `<up>` and `<down>` are even smarter! They recall the
command-line whose beginning matches the current command-line. E.g. `:echo <up>`
may change to `:echo "Vim rocks!"`.

Of course, I don't want you to reach to the arrow keys, just map it instead:

```vim
cnoremap <c-n>  <down>
cnoremap <c-p>  <up>
```

I depend on this behaviour several times a day.

## Saner CTRL-L

By default, `<c-l>` clears and redraws the screen (like `:redraw!`). The
following mapping does the same, plus de-highlighting the matches found via `/`,
`?` etc., plus fixing syntax highlighting (sometimes Vim loses highlighting due
to complex highlighting rules), plus force updating the syntax highlighting in
diff mode:

```vim
nnoremap <leader>l :nohlsearch<cr>:diffupdate<cr>:syntax sync fromstart<cr><c-l>
```

## Disable audible and visual bells

```vim
set noerrorbells
set novisualbell
set t_vb=
```

See [Vim Wiki: Disable beeping](http://vim.wikia.com/wiki/Disable_beeping).

## Quickly move current line

Sometimes I need a quick way to move the current line above or below:

```vim
nnoremap [e  :<c-u>execute 'move -1-'. v:count1<cr>
nnoremap ]e  :<c-u>execute 'move +'. v:count1<cr>
```

These mappings also take a count, so `2]e` moves the current line 2 lines below.

## Quickly add empty lines

```vim
nnoremap [<space>  :<c-u>put! =repeat(nr2char(10), v:count1)<cr>'[
nnoremap ]<space>  :<c-u>put =repeat(nr2char(10), v:count1)<cr>
```

Now `5[<space>` inserts 5 blank lines above the current line.

## Quickly edit your macros

이것 진짜 멋져요. 맵핑은 레지스터 하나를 쓰죠(혹은 디폴트로 `*`) 그리고 
명령어 창에 그것을 열죠. 레지스터를 편집하고 나면 `<cr>`을 누르세요.

저는 매크로를 녹화하는 동안 실수(오타)를 고치기 위해서 이걸 사용합니다.

```vim
nnoremap <leader>m  :<c-u><c-r><c-r>='let @'. v:register .' = '. string(getreg(v:register))<cr><c-f><left>
```

`<leader>m`나 `"q<leader>m`로 사용하세요.

`<c-r>`이 삽입된 것을 재확인 하기 위해서 `<c-r><c-r>`를 사용한 걸 보세요. 
`:h c_^R^R`에서 볼 수 있습니다.

## Quickly jump to header or source file

This technique can probably be applied to many filetypes. It sets _file marks_
(see `:h marks`) when leaving a source or header file, so you can quickly jump
back to the last accessed one by using `'C` or `'H` (see `:h 'A`).

```vim
autocmd BufLeave *.{c,cpp} mark C
autocmd BufLeave *.h       mark H
```

**NOTE**: The info is saved in the viminfo file, so make sure that `:set
viminfo?` includes `:h viminfo-'`.

## Quickly change font size in GUI

I think this was taken from tpope's config:

```vim
command! Bigger  :let &guifont = substitute(&guifont, '\d\+$', '\=submatch(0)+1', '')
command! Smaller :let &guifont = substitute(&guifont, '\d\+$', '\=submatch(0)-1', '')
```

## Change cursor style dependent on mode

I like to use a block cursor in normal mode, i-beam cursor in insert mode, and
underline cursor in replace mode.

```vim
if empty($TMUX)
  let &t_SI = "\<Esc>]50;CursorShape=1\x7"
  let &t_EI = "\<Esc>]50;CursorShape=0\x7"
  let &t_SR = "\<Esc>]50;CursorShape=2\x7"
else
  let &t_SI = "\<Esc>Ptmux;\<Esc>\<Esc>]50;CursorShape=1\x7\<Esc>\\"
  let &t_EI = "\<Esc>Ptmux;\<Esc>\<Esc>]50;CursorShape=0\x7\<Esc>\\"
  let &t_SR = "\<Esc>Ptmux;\<Esc>\<Esc>]50;CursorShape=2\x7\<Esc>\\"
endif
```

This simply tells Vim to print a certain sequence of characters ([escape
sequence](https://en.wikipedia.org/wiki/Escape_sequence)) when entering/leaving
insert mode. The underlying terminal, or programs like
[tmux](https://tmux.github.io) that sit between Vim and the terminal, will
process and evaluate it.

There's one drawback though: there are many terminal emulator implementations
and not all use the same sequences for doing the same things. The sequences used
above might not work with your implementation. Your implementation might not
even support different cursor styles. Check the documentation.

The example above works with iTerm2.

## Don't lose selection when shifting sidewards

If you select one or more lines, you can use `<` and `>` for shifting them
sidewards. Unfortunately you immediately lose the selection afterwards.

You can use `gv` to reselect the last selection (see `:h gv`), thus you can work
around it like this:

```vim
xnoremap <  <gv
xnoremap >  >gv
```

Now you can use `>>>>>` on your visual selection without any problems.

**NOTE**: The same can be achieved using `.`, which repeats the last change.

## Reload a file on saving

Using [autocmds](#autocmds) you can do anything on saving a file, e.g. sourcing
it in case of a dotfile or running a linter to check for syntactical errors in
your source code.

```vim
autocmd BufWritePost $MYVIMRC source $MYVIMRC
autocmd BufWritePost ~/.Xdefaults call system('xrdb ~/.Xdefaults')
```

## Smarter cursorline

I love the cursorline, but I only want to use it in the current window and not
when being in insert mode:

```vim
autocmd InsertLeave,WinEnter * set cursorline
autocmd InsertEnter,WinLeave * set nocursorline
```

## Faster keyword completion

The keyword completion (`<c-n>`/`<c-p>`) tries completing whatever is listed in
the `'complete'` option. By default, this also includes tags (which can be
annoying) and scanning all included files (which can be very slow). If you can
live without these things, disable them:

```vim
set complete-=i   " disable scanning included files
set complete-=t   " disable searching tags
```

## Cosmetic changes to colorschemes

Always use a dark gray statusline, no matter what colorscheme is chosen:

```vim
autocmd ColorScheme * highlight StatusLine ctermbg=darkgray cterm=NONE guibg=darkgray gui=NONE
```

This triggers every time you use `:colorscheme ...`. If you want it to trigger
only for a certain colorscheme:

```vim
autocmd ColorScheme desert highlight StatusLine ctermbg=darkgray cterm=NONE guibg=darkgray gui=NONE
```

This triggers only for `:colorscheme desert`.

# Commands

Useful commands that are good to know. Use `:h :<command name>` to learn more
about them, e.g. `:h :global`.

## :global and :vglobal

Execute a command on all matching lines. E.g. `:global /regexp/ print` will use
`:print` on all lines that contain "regexp".

Fun fact: You probably all know good old grep, the filter program written by Ken
Thompson. What does it do? It prints all lines matching a certain regular
expression! Now guess the short form of `:global /regexp/ print`? That's right!
It's `:g/re/p`. Ken Thompson was inspired by vi's `:global` when he wrote grep.

Despite its name, `:global` only acts on all lines by default, but it also takes
a range. Assume you want use `:delete` on all lines from the current line to the
next blank line (matched by the regular expression `^$`) that contain "foo":

```vim
:,/^$/g/foo/d
```

For executing commands on all lines that do _not_ match a given pattern, use
`:global!` or its alias `:vglobal` (think _inVerse_) instead.

## :normal and :execute

These commands are commonly used in Vim scripts.

With `:normal` you can do normal mode mappings from the command-line. E.g.
`:normal! 4j` will make the cursor go down 4 lines (without using any custom
mapping for "j" due to the "!").

Mind that `:normal` also takes a [range](#ranges), so `:%norm! Iabc` would
prepend "abc" to every line.

With `:execute` you can mix commands with expressions. Assume you edit a C
source file and want to switch to its header file:

```vim
:execute 'edit' fnamemodify(expand('%'), ':r') . '.h'
```

Both commands are often used together. Assume you want to make the cursor go
down "n" lines:

```vim
:let n = 4
:execute 'normal!' n . 'j'
```

## :redir and execute()

Many commands print messages and `:redir` allows to redirect that output. You
can redirect to files, [registers](#registers) or variables.

```vim
:redir => var
:reg
:redir END
:echo var
:" For fun let's also put it onto the current buffer.
:put =var
```

In Vim 8 there is an even shorter way:

```vim
:put =execute('reg')
```

Help:

```
:h :redir
:h execute()
```

# Debugging

## General tips

If you encounter a strange behaviour, try reproducing it like this:

```
vim -u NONE -N
```

This will start Vim without vimrc (thus default settings) and in nocompatible
mode (which makes it use Vim defaults instead of vi defaults). (See `:h
--noplugin` for other combinations of what to load at start.)

If you can still reproduce it now, it's most likely a bug in Vim itself! Report
it to the [vim_dev](https://groups.google.com/forum/#!forum/vim_dev) mailing
list. Most of the time the issue won't be resolved at this time and you'll have
to further investigate.

Plugins often introduce new/changed/faulty behaviour. E.g. if it happens on
saving, check `:verb au BufWritePost` to get a list of potential culprits.

If you're using a plugin manager, comment them out until you find the culprit.

Issue is still not resolved? If it's not a plugin, it must be your other
settings, so maybe your options or autocmds etc.

Time to use binary search. Repeatedly split the search space in two until you
find the culprit line. Due to the nature of binary division, it won't take many
steps.

In practice, it works like this: Put the `:finish` command in the middle of your
vimrc. Vim will skip everything after it. If it still happens, the problem is in
the active upper half. Move the `:finish` to the middle of _that_ half.
Otherwise, the issue is in the inactive lower half. Move the `:finish` to the
middle of _that_ half. And so on.

## Verbosity

Another useful way for observing what Vim is currently doing is increasing the
verbosity level. Currently Vim supports 9 different levels. See `:h 'verbose'`
for the full list.

```vim
:e /tmp/foo
:set verbose=2
:w
:set verbose=0
```

This would show all the files that get sourced, e.g. the undo file or various
plugins that act on saving.

If you only want increase verbosity for a single command, there's also
`:verbose`, which simply gets put in front of any other command. It takes the
verbosity level as count and defaults to 1:

```vim
:verb set verbose
"  verbose=1
:10verb set verbose
"  verbose=10
```

It's very often used with its default verbosity level 1 to show where an option
was set last:

```vim
:verb set ai?
"      Last set from ~/.vim/vimrc
```

Naturally, the higher the verbosity level the more overwhelming the output. But
fear no more, you can simply redirect the output to a file:

```vim
:set verbosefile=/tmp/foo | 15verbose echo "foo" | vsplit /tmp/foo
```

You can also enable verbosity at starting time, with the `-V` option. It
defaults to verbosity level 10. E.g. `vim -V5`.

## Profiling startup time

Vim startup feels slow? Time to crunch some numbers:

```
vim --startuptime /tmp/startup.log +q && vim /tmp/startup.log
```

The first column is the most important as it shows the elapsed absolute time. If
there is a big jump in time between two lines, the second line is either a very
big file or a file with faulty VimL code that is worth investigating.

## Profiling at runtime

Required [feature](#what-kind-of-vim-am-i-running): `+profile`

Vim provides a built-in capability for profiling at runtime and is a great way
to find slow code in your environment.

The `:profile` command takes a bunch of sub-commands for specifying what to
profile.

If you want to profile _everything_, do this:

    :profile start /tmp/profile.log
    :profile file *
    :profile func *
    <do something in Vim>
    :qa

Vim keeps the profiling information in memory and only writes it out to the
logfile on exit. (Neovim has fixed this using `:profile dump`).

Have a look at `/tmp/profile.log`. All code that was executed during profiling
will be shown. Every line, how often it was executed and how much time it took.

Jump to the bottom of the log. Here are two different sections `FUNCTIONS SORTED
ON TOTAL TIME` and `FUNCTIONS SORTED ON SELF TIME` that are worth gold. At a
quick glance you can see which functions are taking the longest.

You can use `:profile` during startup as well:

    $ vim --cmd 'prof start prof.log | prof file * | prof func *' test.c
    :q
    $ tail -50 prof.log

## Debugging Vim scripts

If you ever used a command-line debugger before, `:debug` will quickly feel
familiar.

Simply prepend `:debug` to any other command and you'll be put into debug mode.
That is, the execution will stop at the first line about to be executed and that
line will be displayed.

See `:h >cont` and below for the 6 available debugger commands and note that,
like in gdb and similar debuggers, you can also use their short forms: `c`, `q`,
`n`, `s`, `i`, and `f`.

Apart from that those, you're free to use any Vim command, e.g. `:echo myvar`,
which gets executed in the context of the current position in the code.

You basically get a
[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) by
simply using `:debug 1`.

It would be a pain if you had to single-step through every single line, so of
course we can define breakpoints, too. (Breakpoints are called breakpoints,
because the execution stops when they're hit, thus you can simply skip code
you're not interested in.) See `:h :breakadd`, `:h :breakdel`, and `:h
:breaklist` for further details.

Let's assume you want to know what code is run every time you save a file:

```vim
:au BufWritePost
" signify  BufWritePost
"     *         call sy#start()
:breakadd func *start
:w
" Breakpoint in "sy#start" line 1
" Entering Debug mode.  Type "cont" to continue.
" function sy#start
" line 1: if g:signify_locked
>s
" function sy#start
" line 3: endif
>
" function sy#start
" line 5: let sy_path = resolve(expand('%:p'))
>q
:breakdel *
```

As you can see, using `<cr>` will repeat the previous debugger command, `s` in
this case.

`:debug` can be used in combination with the [verbose](#verbosity) option.

## Debugging syntax files

Syntax files are often the cause for slowdowns due to wrong and/or complex
regular expressions. If the `+profile` [feature](#what-kind-of-vim-am-i-running)
is compiled in, Vim provides the super useful `:syntime` command.

```vim
:syntime on
" hit <c-l> a few times to redraw the window which causes the syntax rules to get applied again
:syntime off
:syntime report
```

The output contains important metrics. E.g. you can see which regexp takes too
long and should be optimized or which regexps are used all the time but never
even match.

See `:h :syntime`.

# Miscellaneous

## Additional resources

| Resource | Description |
|----------|-------------|
| [Seven habits of effective text editing](http://www.moolenaar.net/habits.html) | By Bram Moolenaar, the author of Vim. |
| [Seven habits of effective text editing 2.0 (PDF)](http://www.moolenaar.net/habits_2007.pdf) | See above. |
| [IBM DeveloperWorks: Scripting the Vim editor](http://www.ibm.com/developerworks/views/linux/libraryview.jsp?sort_order=asc&sort_by=Title&search_by=scripting+the+vim+editor) | Five-part series on Vim scripting. |
| [Learn Vimscript the Hard Way](http://learnvimscriptthehardway.stevelosh.com) | Develop a Vim plugin from scratch. |
| [Practical Vim (2nd Edition)](http://www.amazon.com/Practical-Vim-Edit-Speed-Thought/dp/1680501275/) | Hands down the best book about Vim. |
| [Why, oh WHY, do those #?@! nutheads use vi?](http://www.viemu.com/a-why-vi-vim.html) | Common misconceptions explained. |
| [Your problem with Vim is that you don't grok vi](http://stackoverflow.com/a/1220118) | Concise, informative and correct. A real gem. |

#### Screencasts

- [vimcasts.org](http://vimcasts.org/episodes/archive)
- [By wincent](https://www.youtube.com/channel/UCXPHFM88IlFn68OmLwtPmZA)
- [By Derek Wyatt](http://derekwyatt.org/vim/tutorials/index.html)

## Vim distributions

Vim distributions are bundles of custom settings and plugins for Vim.

More advanced users know how to configure their editor anyway, so distributions
are mostly targeted at beginners. If you think about that, it's quite
paradoxical though: Making it easier by adding even more things to learn about?

I know that many people don't want to spend hours and hours on customizing an
editor (and actually you never stop customizing your vimrc when you finally got
hooked), but eventually you only get efficient in Vim when you take the time to
learn it properly.

Repeat after me: "A programmer should know their tools."

Anyway, if you know what you're doing, you might draw some inspiration from
looking at a few distributions:

- [cream](http://cream.sourceforge.net)
- [janus](https://github.com/carlhuda/janus.git)
- [spacevim](https://github.com/SpaceVim/SpaceVim)
- [spf13](https://github.com/spf13/spf13-vim)

## Standard plugins

Many people are surprised by the fact that Vim comes with a handful of standard
plugins. Some get loaded by default (`:e $VIMRUNTIME/plugin`) and some are not
(`:e $VIMRUNTIME/pack/dist/opt`). Read `:h pack-add` on how to source the
latter.

Most of the plugins that get loaded by default will never get used, though.
Disable them as you see fit. They will still be shown as sourced
(`:scriptnames`), but only the first lines actually get read before Vim bails
out. No further code (mappings, commands, logic) will be processed.

| Plugin     | Disable it using..                  | Help |
|------------|-------------------------------------|------|
| 2html      | `let g:loaded_2html_plugin = 1`     | `:h 2html` |
| getscript  | `let g:loaded_getscriptPlugin = 1`  | `:h pi_getscript` |
| gzip       | `let g:loaded_gzip = 1`             | `:h pi_gzip` |
| logipat    | `let g:loaded_logipat = 1`          | `:h pi_logipat` |
| matchparen | `let g:loaded_matchparen = 1`       | `:h pi_paren` |
| netrw      | `let g:loaded_netrwPlugin = 1`      | `:h pi_netrw` |
| rrhelper   | `let g:loaded_rrhelper = 1`         | `:e $VIMRUNTIME/plugin/rrhelper.vim` |
| spellfile  | `let g:loaded_spellfile_plugin = 1` | `:h spellfile.vim` |
| tar        | `let g:loaded_tarPlugin = 1`        | `:h pi_tar` |
| vimball    | `let g:loaded_vimballPlugin = 1`    | `:h pi_vimball` |
| zip        | `let g:loaded_zipPlugin = 1`        | `:h pi_zip` |

## Map CapsLock to Control

CapsLock belongs to the most useless keys on your keyboard, but it's much easier
to reach than the Control key, since it lies on your [home
row](https://raw.githubusercontent.com/mhinz/vim-galore/master/static/images/content-homerow.png).
Mapping CapsLock to Control is a great way to prevent or at least reduce
[RSI](https://de.wikipedia.org/wiki/Repetitive-Strain-Injury-Syndrom) if you
program a lot.

Attention: When you get used to it, you can't live without it anymore.

**macOS**:

`System Preferences -> Keyboard -> Keyboard Tab -> Modifier Keys`. Change
"CapsLock" to "Control".

**Linux**:

To change the keys in X, put this in your `~/.xmodmap`:

    remove Lock = Caps_Lock
    keysym Caps_Lock = Control_L
    add Control = Control_L

Afterwards source it via `$ xmodmap ~/.xmodmap`.

An alternative would be using [caps2esc](https://github.com/oblitum/caps2esc) or
[xcape](https://github.com/alols/xcape).

**Windows**:

See [superuser.com: Map Caps-Lock to Control in Windows
8.1](http://superuser.com/questions/764782/map-caps-lock-to-control-in-windows-8-1).

## Generating HTML from buffer

Generate HTML from any buffer using `:TOhtml` from the 2html [standard
plugin](#standard-plugins). The output can be used for printing or easy web
publishing.

The command creates a new buffer of the same name with `.html` appended. The
colors are the same as seen in Vim. They depend on the
[colorscheme](#colorschemes).

The plugin knows several options to finetune the output, e.g. for setting the
encoding and font.

See `:h :TOhtml`.

## Easter eggs

| Command   | Message |
|-----------|---------|
| `:Ni!` | `Do you demand a shrubbery?` |
| `:h 'sm'` | `NOTE: Use of the short form is rated PG.` |
| `:h 42` | `What is the meaning of life, the universe and everything? Douglas Adams, the only person who knew what this question really was about is now dead, unfortunately.  So now you might wonder what the meaning of death is...` |
| `:h UserGettingBored` | `When the user presses the same key 42 times. Just kidding! :-)` |
| `:h bar` | `Ceci n'est pas une pipe.` |
| `:h holy-grail` | `You found it, Arthur!` |
| `:h map-modes` | `:nunmap can also be used outside of a monastery.` |
| `:help!` | `E478: Don't panic!` (Glitch? When used in a help buffer (`buftype=help`) this works like `:h help.txt` instead.) |
| `:smile` | Try it out yourself. ;-) Added in 7.4.1005. |

## Why hjkl for navigation?

When [Bill Joy](https://en.wikipedia.org/wiki/Bill_Joy) created
[vi](https://en.wikipedia.org/wiki/Vi), a predecessor of Vim, he did it on a
[ADM-3A](https://en.wikipedia.org/wiki/ADM-3A) which had no extra cursor buttons
but used, you might already guessed it, hjkl instead.

Keyboard layout: [click](https://raw.githubusercontent.com/mhinz/vim-galore/master/static/images/content-adm-3a-layout.jpg)

This also shows why `~` is used to denote the home directory on Unix systems.

# Common problems

## Editing small files is slow

There are two things which can have a huge impact on performance:

1. Complex **regular expressions**. Particular the Ruby syntax file caused
   people to have slowdowns in the past. (Also see [Debugging syntax files](#debugging-syntax-files).)
2. **Screen redraws**. Some features force all lines to redraw.

| Typical culprit | Why? | Solution? |
|-----------------|------|-----------|
| `:set cursorline`        | Causes all lines to redraw. | `:set nocursorline` |
| `:set cursorcolumn`      | Causes all lines to redraw. | `:set nocursorcolumn` |
| `:set relativenumber`    | Causes all lines to redraw. | `:set norelativenumber` |
| `:set foldmethod=syntax` | If the syntax file is slow already, this makes it even worse. | `:set foldmethod=manual`, `:set foldmethod=marker` or [FastFold](https://github.com/Konfekt/FastFold) |
| `:set synmaxcol=3000`    | Due to internal representation, Vim has problems with long lines in general. Highlights columns till column 3000. | `:set synmaxcol=200` |
| matchparen.vim           | Loaded by default. Uses regular expressions to find the accompanying parenthesis. | Disable plugin: `:h matchparen` |

**NOTE**: You only need to do this if you experience actual performance
drawbacks. In most cases using the things mentioned above is absolutely fine.

## Editing huge files is slow

The biggest issue with big files is, that Vim reads the whole file at once. This
is done due to how buffers are represented internally.
([Discussion on vim_dev@](https://groups.google.com/forum/#!topic/vim_dev/oY3i8rqYGD4/discussion))

If you only want to read, `tail hugefile | vim -` is a good workaround.

If you can live without syntax, settings and plugins for the moment:

```
$ vim -u NONE -N
```

This should make navigation quite a lot faster, especially since no expensive
regular expressions for syntax highlighting are used. You should also tell Vim
not to use swapfiles and viminfo files to avoid long delays on writing:

```
$ vim -n -u NONE -i NONE -N
```

Putting it in a nutshell, try to avoid using Vim when intending to write really
huge files. :\

## Bracketed paste (or why do I have to set 'paste' all the time?)

Bracketed paste mode allows terminal emulators to distinguish between typed text
and pasted text.

Did you ever tried pasting code into Vim and afterwards everything seemed messed
up?

This only happens if you paste via `cmd+v`, `shift-insert`, `middle-click` etc.
because then you're just throwing text at the terminal emulator. Vim doesn't
know that you just pasted the text, it thinks you're an extremely fast typist.
Accordingly, it tries to indent the lines and fails.

Obviously this is not an issue, if you paste using Vim's registers, e.g. `"+p`,
because then Vim knows that you're actually pasting.

To workaround this, you have to `:set paste`, so it gets pasted as-is. See `:h
'paste'` and `:h 'pastetoggle'`.

If you're fed up with toggling `'paste'` all the time, have a look at this fine
plugin that does it for you:
[bracketed-paste](https://github.com/ConradIrwin/vim-bracketed-paste).

Additional read from the same author as the plugin:
[here](http://cirw.in/blog/bracketed-paste).

**Neovim**: Neovim tries to make all of this much more seamless and sets
bracketed paste mode automatically if the terminal emulator supports it.

## Delays when using escape key in terminal

If you live in the command-line, you probably use a so-called _terminal
emulator_ like xterm, gnome-terminal, iTerm2, etc. (opposed to a real
[terminal](https://en.wikipedia.org/wiki/Computer_terminal)).

Like their ancestors, terminal emulators use [escape
sequences](https://en.wikipedia.org/wiki/Escape_sequence) (or _control
sequences_) to control things like moving the cursor, changing text colors, etc.
They're simply strings of ASCII characters starting with an escape character
(displayed in [caret notation](https://en.wikipedia.org/wiki/Caret_notation) as
`^[`). When such a string arrives, the terminal emulator looks up the
accompanying action in the [terminfo](https://en.wikipedia.org/wiki/Terminfo)
database.

To make the problem clearer, I'll explain mapping timeouts first. They always
happen when there's ambiguity between mappings:

```vim
:nnoremap ,a  :echo 'foo'<cr>
:nnoremap ,ab :echo 'bar'<cr>
```

Both mappings work as expected, but when typing `,a`, there will be a delay of 1
second, because Vim waits whether the user keys in another `b` or not.

Escape sequences pose the same problem:

- `<esc>` is used a lot for returning to normal mode or quitting an action.
- Cursor keys are encoded using escape sequences.
- Vim expects <kbd>Alt</kbd> (also called _Meta key_) to send a proper 8-bit
  encoding with the high bit set, but many terminal emulators don't support it
  (or don't enable it by default) and send an escape sequence instead.

You can test the above like this: `vim -u NONE -N` and type `i<c-v><left>` and
you'll see a sequence inserted that starts with `^[` which denotes the escape
character.

Putting it in a nutshell, Vim has a hard time distinguishing between a typed
`<esc>` character and a proper escape sequence.

By default, Vim uses `:set timeout timeoutlen=1000`, so it delays on ambiguity
of mappings _and_ key codes by 1 second. This is a sane value for mappings, but
you can define the key code timeout on its own which is the most common
workaround for this entire issue:

```vim
set timeout           " for mappings
set timeoutlen=1000   " default value
set ttimeout          " for key codes
set ttimeoutlen=10    " unnoticeable small value
```

Under `:h ttimeout` you find a small table showing the relationship between
these options.

If you're using tmux between Vim and your terminal emulator, also put this in
your `~/.tmux.conf`:

```tmux
set -sg escape-time 0
```

## Function search undo

- A search pattern in a command (`/`, `:substitute`, ...) changes the "last used
  search pattern". (It's saved in the `/` register; print it with `:echo @/`).
- A simple text change can be redone with `.`. (It's saved in the `.` register;
  print it with `:echo @.`).

Both things are _not_ the case, if you do them from a function, though! Thus you
can't easily highlight words from a function or redo the text changes made by
it.

Help: `:h function-search-undo`

# Technical quirks

## Newline used for NUL

NUL characters (`\0`) in a file, are stored as newline (`\n`) in memory and
displayed in a buffer as `^@`.

See `man 7 ascii` and `:h NL-used-for-Nul` for more information.

# Terminology

## Vim script? Vimscript? VimL?

`Vim script`, `Vimscript`, and `VimL` all refer to the same thing: The
programming language used for scripting Vim. Even though
[8.0.360](https://github.com/vim/vim/commit/b544f3c81f1e6a50322855681ac266ffaa8e313c)
changed all references to `VimL` to `Vim script`, which can now be considered
the official term, `VimL` is still widespread all over the internet.

No matter which term you use, everyone will understand it.
