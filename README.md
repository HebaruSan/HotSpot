# Hot Spot [![AppVeyor Status][build-badge-appveyor]][build-appveyor] [![Travis CI Status][build-badge-travis]][build-travis]

**Hot Spot** is a [MIT-licensed](LICENSE.md) Kerbal Space Program mod that displays better thermal data. It currently
supports the following metrics:

- Temperature
- Thermal Rate

Hot Spot can display three kinds of temperatures:

- *Skin Temperature* &mdash; The temperature of the exposed surface of a part.
- *Internal Temperature* &mdash; The temperature of the interior of a part.
- *Core Temperature* &mdash; The temperature of the core of a part (for those parts with cores such as ISRU parts).

Thermal rate is the rate at which thermal energy is added or removed from a part. It is measured as energy per unit
time, i.e. [*power*][wiki-power]. Positive thermal rates indicate a part is gaining thermal energy, negative thermal
rates indicate a part is losing thermal energy. There are multiple kinds of thermal rates:

- *Internal Thermal Rate* &mdash; The change in thermal energy due to reactions/processes occuring within the part itself.
- *Conductive Thermal Rate* &mdash; The change in thermal energy due to being in contact with other parts.
- *Convective Thermal Rate* &mdash; The change in thermal energy due to being in contact with a fluid, like the atmosphere.
- *Radiative Thermal Rate* &mdash; The change in thermal energy due to the emission or absorption of light.
- *Thermal Rate* &mdash; An aggregate value of the four previous rates.
- *Skin to Internal Thermal Rate* The change in thermal energy due to transfer from the part's skin to its interior.
- *Internal to Skin Thermal Rate* The change in thermal energy due to transfer from the part's interior to its skin.

These metrics are can be displayed in one of two ways:

### Context Menu
Hot Spot will add the metrics to the right-click context menu of all parts. Both the current and maximum temperature
of a part are displayed and the unit can be changed between [Kelvin][wiki-kelvin], [Celsius][wiki-celsius],
[Rankine][wiki-rankine], and [Fahrenheit][wiki-fahrenheit]. Thermal rates are always displayed in units of Kilowatts
(kW).

### Part Overlay

Hot Spot will also replace the stock *Thermal Debug Overlay* with one displaying the metric of the user's choice and
will replace the standard black body color gradient with one that is more intuitive.

#### Temperature
The color gradient used for temperature is as follows:

- Purple (0K)
- Blue (273.2K)
- Transparent (287.5K)
- Yellow (373.13K)
- Orange (0.67×*Maximum*)
- Red (*Maximum*)

The *Maximum* value depends on the scheme used:

- *Part Absolute* - The maximum temperature of the current part.
- *Vessel Current* - The maximum current temperature of any part in the vessel.
- *Vessel Absolute* - The maximum temperature of any part in the vessel.

#### Ideal Temperature

The color gradient used for ideal temperatures is as follows:

- Purple (0K)
- Blue (0.8×*Ideal*)
- Green (*Ideal*)
- Yellow (1.2×*Ideal*)
- Red (*Maximum*)

Where *Ideal* is the part's "ideal" temperature, e.g. for resource converters its the temperature at which conversion
is maximally efficient, and *Maximum* is the maximum temperature for the current part.

#### Thermal Rate
The color gradient used for thermal rates is as follows:

- Purple (*Vessel Current Minimum*, if negative)
- Blue (0.1×*Vessel Current Minimum*, if negative)
- Transparent (0)
- Yellow (0.1×*Vessel Current Maxmimum*, if positive)
- Orange (0.5×*Vessel Current Maxmimum*, if positive)
- Red (*Vessel Current Maxmimum*, if positive)

## Installation
### CKAN
Hot Spot's CKAN identifier is `HotSpot`. It may be installed from the command line with:

```
> ckan install HotSpot
```

It can also be installed from the GUI.

### Manual
1. Download the distribution package from [GitHub][github-releases].
2. Extract the contents of the archive to your KSP directory. This should create an `HotSpot` directory under
the `<KSP>/GameData` directory.
3. Follow the installation instructions for all dependencies.

#### Dependencies
- [Module Manager][module-manager]

## Usage
Right-clicking on parts will display enabled metrics. Pressing the `TOGGLE_TEMP_OVERLAY` key (`F11` by default)
enables metric overlays. Dynamic configuration can be done by pressing the Hot Spot button in the application
launcher.

## Configuration
More features of Hot Spot can be configured by creating Module Manager patches against the default settings stored in
`<KSP>/GameData/HotSpot/Configuration/HotSpot.cfg`. How to use Module Manager is outside the scope of this README,
please see the Module Manager documentation for more information.

[build-appveyor]: https://ci.appveyor.com/project/Apokee/hotspot/branch/develop
[build-travis]: https://travis-ci.org/Apokee/HotSpot
[build-badge-appveyor]: https://ci.appveyor.com/api/projects/status/ik9la5jusinnpu5n/branch/develop?svg=true
[build-badge-travis]: https://api.travis-ci.org/Apokee/HotSpot.svg?branch=develop
[github-releases]: https://github.com/Apokee/HotSpot/releases
[module-manager]: http://forum.kerbalspaceprogram.com/threads/55219
[wiki-celsius]: https://en.wikipedia.org/wiki/Celsius
[wiki-fahrenheit]: https://en.wikipedia.org/wiki/Fahrenheit
[wiki-kelvin]: https://en.wikipedia.org/wiki/Kelvin
[wiki-power]: https://en.wikipedia.org/wiki/Power_%28physics%29
[wiki-rankine]: https://en.wikipedia.org/wiki/Rankine_scale
