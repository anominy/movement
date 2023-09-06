[latest-release]: https://github.com/anominy/movement/releases/latest
[layout-def_36th]: https://github.com/anominy/movement/blob/main/layout/def.cfg#L36
[redmoon-youtube]: https://www.youtube.com/@ReDMooNTVV

## Movement Configs
I would love to share the result of my 5-day work.
This is a well commented & modular set of movement
configs that cover most of or all the movement engine
mechanics of the Counter-Strike game series.

If you're a new to this topic, I would recommend watching
the [ReDMooN][redmoon-youtube]'s YouTube channel and videos
describing the VNL mode.

<br>
-- I kindly ask, follow the installation & setup instructions.


### Install
1. Download the latest version from the [releases][latest-release] page.
2. Extract the `/movement/` folder to your `/csgo/cfg/` game directory.

#### Overview
```shell
Tree .\movement\ /F
```
```text
C:\PROGRAM FILES (X86)\STEAM\STEAMAPPS\COMMON\COUNTER-STRIKE GLOBAL OFFENSIVE\CSGO\CFG\MOVEMENT
│   lagdef.cfg
│   stddef.cfg
│   wjdef.cfg
│
├───gokz
│       def.cfg
│
├───hsw
│       lagdef.cfg
│       stddef.cfg
│
├───layout
│   │   def.cfg
│   │   std.cfg
│   │
│   └───default
│           def.cfg
│           std.cfg
│
└───lib
        include.cfg
        internal.cfg
```


### Setup
1. Open the `/movement/layout/def.cfg` file.
2. Edit an alias in the [36th line][layout-def_36th] w/ your actual mouse wheel bindings.
    * If you don't have them, replace it w/ `unbind` command.
3. Open the `/csgo/cfg/autoexec.cfg` file.
    * If you don't have one, create then.
    * Append w/ `exec movement/lib/include.cfg` command.
    * Append w/ needed definitions — `include__std_def`, `include__hsw_def`, etc.

#### Overview
```shell
.\autoexec.cfg
```
```text
// For example, if your existing autoexec config looks like this.
// + ------------------------------------------------------------
// | Put `exec movement/lib/include.cfg` & `include__std_def`
// |  at the end of this file to include standard definition config.



// === [ BEGIN ~ AUTOEXEC.CFG ] ===

fps_max 0
cl_threaded_bone_setup 1
cl_interpolate 0
cl_interp_ratio 0
cl_interp 0
cl_spec_show_bindings 0
cl_server_graphic1_enable 0
cl_server_graphic2_enable 0
cl_sanitize_muted_players 0

alias vm "viewmodel_fov 68; viewmodel_offset_x 2; viewmodel_offset_y 2; viewmodel_offset_z -2; cl_bob_lower_amt 8; cl_bobamt_lat 0.1; cl_bobamt_vert 0.1"

alias i0 "cl_interpolate 0; cl_interp_ratio 0; cl_interp 0"
alias i1 "cl_interpolate 1; cl_interp_ratio 2; cl_interp 1"

// === [ END ~ AUTOEXEC.CFG ] ===



// For example, here is my setup that I currently use for kreedz, bhop and movement modes.
// + -------------------------------------------------------------------------------------
// | I include other definition configs dynamically via the game console when necessary.
// |  Like playing the S-HSW style on bhop:
// |    * `include__hsw_def`
// |    * `bind [w/s/d/a] +[ls/rs]_hsw_null_[forward/back/moveright/moveleft]`
// |    * `bind space +hsw_[mj/lj]_fw`
// |
// |  Or statting the WeirdJump style on VNL:
// |    * `include__std_wj`
// |    * `bind [w/s/d/a] +wj_[fw/sw]_null_[forward/back/moveright/moveleft]`
// |
// |  Or just playing the CS:GO MatchMaking:
// |    * `include__std_def`
// |    * `bind [w/s/d/a] +null_[forward/back/moveright/moveleft]`
// |    * `bind space +lj_fw`



// === [ BEGIN ~ SETUP ] ===

exec movement/lib/include.cfg         // Adds `include__` prefixed aliases to be able to include
                                      //  the configs only once.
exec movement/layout/default/def.cfg  // Overrides a layout-config definition w/ a default one.
exec movement/layout/default/std.cfg  // Overrides a layout-config key mappings w/ a default one.

include__std_def                      // Includes a standard definition config.

// === [ END ~ SETUP ] ===
```


### Definitions
* Root `/movement/`
  * include__std_def
    * LongJump
    * CrouchJump
    * MiniJump
    * JumpBug
    * CrouchBug
    * Nulls
  * include__std_wj
    * WeirdJump
  * include__std_lag
    * LadderGlide
* Half-SideWays `/movement/hsw/`
  * include__hsw_def
    * LongJump
    * CrouchJump
    * MiniJump
    * Nulls
  * include__hsw_lag
    * LadderGlide
* GOKZ `/movement/gokz/`
  * include__gokz_def
    * TP on course start
    * Danvari technique
    

### Layouts
The `/movement/layout/` module contains anything related
to the binding layouts/key mappings. You can create & place
your own layout-configs and exec them in `autoxec.cfg`.
There also a pre-defined standard layout in the `/default/`
directory that you can explore or even use!


### Library
The `/movement/lib/` module contains anything related to the
project structure & internal functional. You don't have to be
aware of this one as an end user.


### License
Licensed under the [CC BY-NC-ND 4.0 license](./LICENSE).
