# CACmb Toolkit

This toolkit contains Python programs that allow for CAC data file pre/post processing outside the scope of the [core Fortran code](https://gitlab.com/aselimov/cacmb).

See `requirements.txt` for package dependencies. You can use pip to install these directly.

## convertor (_under development_)



The conversion type is inferred from file extension provided as input and output arguments

Currently supported conversions:

| From      | To        | Notes      |
| ------    | ------    | ------     |
| *.nodal   | *.cac     | readable by LAMMPS `read_data`     |
|           | *.last    | mixed-resolution NEB replica |
|           | *.xyz     | Extended XYZ format (supports --virial flag)|
|           | *.cacovito| visualization of CAC nodes in OVITO     |
| *.dump    | *.last    | LAMMPS NEB replica format     |
| *.cac     | *.cacovito| 
|           | *.xyz     | Extended XYZ format |

### Installation and usage
From this directory...
```
pip install .
```

**Examples**

Command line args are self explanatory
`--replace [-r]` to replace existing without prompting
`--virial [-v]` merges in virial information matching the filename of the dumpfile (*.virial)

```
python -m convertor -h
python -m convertor -i INPUTFILE -o OUTPUTFILE
python -m convertor -i input.nodal -o output.cac -r
```

### \*.cacovito format (deprecated for better *.xyz format)
This format allows you to view CAC structure files in OVITO and color by property. Molecule Type = 1 for nodes, = 0 for atomic DOF.
Load the custom column mapping as:


<img src="colmap.png" width="250">
