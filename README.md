# seasondog

Small tool for saving your progress in watching series.

## Installation

You can install seasondog trough `pip`:
    
    sudo pip install seasondog

## Configuration

First you need to edit **config.py**:

* *DB_PATH*: as default, database located in *~/.seasondog/database*, but you can change it with this variable
* *PLAYER*: you need to provide command line for starting your videoplayer. Two placeholders: videofile and player_args
* *SUB_EXTENSIONS* and *MOVIE_EXTENSIONS*: you can change or add file extensions for lookuping various files.

## Usage

On first call in directory you can provide player args for this directory, where you can setup various per-directory settings (for example - add subtitles). You can use specified functions for file matching in that string, which result substitutes into string.

For example, subtitles for mplayer should be `-sub @subs(subs/ -1 ,)`, that means - *find subtitles in directory sub/, with no limits, and separate all subtitles by symbol `,`*.

Available funtions:

* `@files(path file_limit file_delimeter)` - lookup for files (matching uses similar algoritm, but without extension check) in **path**, limit results to **file_limit** (-1 for unlimited), join all results by **file_delimeter**.
* `@subs(path file_limit file_delimeter)` - just like `@files`, but lookup only subtitles (check by extension).

After you finish setup you can use such commands:

* `sdog` - watch next episode 
* `sdog prev` - watch prev episode
* `sdog watch` - watch current episode
* `sdog set <EPISODE>` - set episode directly and watch it
* `sdog reset` - reset progress and settings for directory
* `sdog status` - get current dir status information
* `sdog args <ARGS>` - set player args in database

And you can use option `-a` for one-time overriding player args. 

## License

Copyright © 2014 Vasiliy Horbachenko

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
