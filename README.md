# Console Snake



## Introduction

The Console Snake game with background music was implemented using C++ and the libraries `libncurses` and `libcplayer`. `libncurses` (new curses) is a programming library providing an application programming interface (API) that allows the programmer to write text-based user interfaces in a terminal-independent manner. [`libcplayer`](https://github.com/leimao/Console-Player)(console player) is a C++ library for playing background audios asynchronously in C++ programs.

## Dependencies

* CMake 3.13.0+
* libncurses 6.1+
* [`libsndfile`](https://github.com/erikd/libsndfile)
* [`libasound`](https://github.com/alsa-project/alsa-lib)
* [`libcplayer`](https://github.com/leimao/Console-Player)

## Files

```
.
├── audios
│   └── bgm.wav
├── CMakeLists.txt
├── demo
│   ├── console_snake_demo.gif
│   ├── console_snake_demo.mp4
│   └── mp42gif.sh
├── LICENSE.md
├── modules
│   └── Console-Player
├── README.md
└── src
    ├── CMakeLists.txt
    ├── game.cpp
    ├── game.h
    ├── main.cpp
    ├── snake.cpp
    └── snake.h
```

## Installation

### Build Docker Image

```bash
$ docker build -f docker/snake.Dockerfile --no-cache --tag=snake:0.0.1 .
```

### Run Docker Container

```bash
$ docker run -it --rm --device /dev/snd -v $(pwd):/mnt snake:0.0.1
```

### Install CMake

Check out [the installation guide from Kitware](https://apt.kitware.com/).

### Install Dependencies

```bash
$ sudo apt-get install libncurses-dev libsndfile-dev libasound2-dev
```

### Install Game

Because the installation requires to use `git submodule`, please `git clone` instead of `download` the repository.

```bash
$ git clone https://github.com/leimao/Console-Snake.git
$ cd Console-Snake
$ git submodule update --init --recursive
$ cmake -B build
$ cmake --build build --target install --config Release
```

## Usages

### Game Rules

Control the snake to eat food as much as possible. You get one point for every food your snake eat. The level of difficulty would increase every 5 points you get.

### Play Game Using Default BGM

```bash
$ cd bin/
$ ./main
```

### Play Game Using Custom BGM

The user is also allowed to use custom BGMs.

```bash
$ cd bin/
$ ./main [bgm_sound_file]
```

Currently the game only supports `wav`, `ogg`, and `flac` audio formats.


## Demo

[![Console Snake Demo](demo/console_snake_demo.gif)](https://www.youtube.com/watch?v=6eUeRn3Mdg4 "Console Snake Demo")

For full demo with sound, please click the demo image and watch the YouTube video.

## Feedbacks

If you have encountered any bug, or have any suggestions for improvements, please open an issue ticket in the repository.


## References

* [CMake Dependency Handling](https://foonathan.net/2016/07/cmake-dependency-handling/)
* [Royalty Free Game BGM - Better Sounds](https://opengameart.org/content/better-sounds-nes-version)

## To-Do List

- [x] Add leader board
- [x] Add background music
- [ ] Allow user to save player name to the leader board
