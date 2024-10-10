+++
title = "Polyclash: A spherical Go Game Program"
description = "We have developed a simple spherical Go program called polyclash. Here, we provide a brief introduction to polyclash and instructions on how to use it."
draft = false

[taxonomies]
tags = ["English"]

[extra]
feature_image = "example.png"
feature = true
+++

Based on previous concepts, we have developed a simple spherical Go program called polyclash. Here, we provide a brief introduction to polyclash and instructions on how to use it.

Polyclash is a reference implementation of spherical Go, developed in Python, and the code is fully [open-source](https://github.com/spherical-go/polyclash).
Polyclash consists of client and server programs, supporting local play, LAN play, and internet play.
Anyone can set up and run their own server; once connected to the server, they can start playing.
For local play, a very rudimentary AI opponent is also included. We won’t cover internet server setup in this article, focusing instead on how to use the program.

### Installation and Startup

Since the program is developed in Python, we need a Python environment version 3.10 or above. Installation is straightforward—simply run the following command:

```
pip install polyclash
```

This will install two local commands: `polyclash-client` and `polyclash-server`.

To launch the client, run:

```
polyclash-client
```

To launch the server, run:

```
polyclash-server
```

### Game Interface

The entire game interface is divided into four parts:

{{img(path='/blog/2024/2024-10-10-polyclash/example.png', width=1238, height=350, op="fit_height")}}

* Game Area: The game area is where the board is located. You can use the mouse to rotate and navigate to a specific area on the sphere, then click on the grid point on the board to place a piece.
* Overview Area: This provides a global overview of the four continents and ocean regions, showing the global distribution of black and white pieces.
* Status Area: Indicates whether it is currently Black's or White's turn and displays the area occupied by each player.
* Coordinate Axis: Shows the orientation of the sphere rotation.

### Gameplay

The default setting of the game is local play against the AI, but due to the simplicity of the AI, it may not provide a highly competitive experience.

The local mode menu also allows for local player-versus-player matches, but this feature is currently limited due to a bug in the evolving version.

Our focus is on network play.

The first step is to start a game through the “Create” option in the “Network Mode” menu.

{{img(path='/blog/2024/2024-10-10-polyclash/create-network-game.png', width=1238, height=350, op="fit_height")}}

Step 2: In the dialog box, enter the network server, such as the reference server "https://sphericalgo.org".

Step 3: Open the server URL "GOSERVER/sphgo/". For our reference server, this means opening "https://sphericalgo.org/sphgo/". On this page, you can obtain the server token.

{{img(path='/blog/2024/2024-10-10-polyclash/server-token.png', width=1238, height=150, op="fit_height")}}

Step 4: Enter the server token in the dialog box and click "Connect." The server will assign a game room with passwords for Black, White, and spectators. Share the Black and White passwords with the respective players using a chat tool.

Step 5: Click “Join” in the “Network Mode” menu to join the game. During the joining process, Black and White players must enter their respective passwords and then click "Ready." The game will start automatically once both players are ready.

{{img(path='/blog/2024/2024-10-10-polyclash/join-network-game.png', width=1238, height=350, op="fit_height")}}

Though the process involves five steps and may seem slightly complex, this is the simplest approach we could think of, as it allows for selecting among multiple servers.