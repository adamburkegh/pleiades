# Pleiades

This project calculates an estimated date for a famous poem by Sappho using the reference to time and the constellation Pleiades. This is from the paper Seasonal Dating of Sappho's 'Midnight Poem' Revisited", reimplemented in notlob and Python. We also try some alternative parameters and account for differences in horizon height. 

A more detailed description is in [dating.lob](astronomical/poetry/dating.lob) in a literate programming style.


## Building and Running

Create isolated environment such as a venv in your preferred way. E.g., for
venv on Windows:

```
python -m venv plei
. plei/Scripts/activate
```


Install Python packages

`pip install -e .`

Build and run notlob. 

`notlob test`

On first run, `skyfield` data files of ~350 Mb will download to `var/`. 
These are required for the project.

This particular project doesn't have a main entry point - the correct execution 
of the tests is the evidence for the assertions in the text.


