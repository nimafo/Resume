# Get access
Read the "Get an account" section on [this page](https://doc.dhpc.tudelft.nl/delftblue/Accounting-and-shares/#get-an-account) and request access if you are a MSc/BSc student.

# Install Radiance
For this tutorial I install version https://github.com/LBNL-ETA/Radiance/releases/tag/rad6R0P2. You can access the latest released version at https://github.com/LBNL-ETA/Radiance.
Copy the 'Source code (tar.gz)' address to clipboard: https://github.com/LBNL-ETA/Radiance/archive/refs/tags/rad6R0P2.tar.gz.  (⚠️ the latest version name might differ.)


In DelftBlue terminal:
1. Download the source code:        
```bash
Wget https://github.com/LBNL-ETA/Radiance/archive/refs/tags/rad6R0P2.tar.gz
```
⚠️ The latest version name might differ.

2. Unpack:  
```bash
tar -xzf rad6R0P2.tar.gz
```

⚠️ The latest version name might differ.

```bash
mkdir ~/.local/lib/ray
``` 
and 
```bash
mkdir ~/.local/lib/ray/meta
```

- Read the `README.txt` in the unpacked folder, according to this instruction do the following:
```bash
cd Radiance-rad6R0P2/
```
```bash
wget https://radsite.lbl.gov/radiance/dist/rad6R0supp.tar.gz
``` 
(At the time of writing this Radiance-online.org server is down, so I accessed the auxilery files from radsite (https://radsite.lbl.gov/radiance/framed.html).

```bash
tar -xzf rad6R0supp.tar.gz
cp -r ray/src/px/tiff src/px/
```
Then install with:
```bash
./makeall install
```
`makeall` will ask you a couple of questions: 

- `What is your preferred editor [vi]?` -> press enter.
- `Where do you want the executables [/usr/local/bin]?` change to `~/.local/bin` -> press enter.
- `Do you understand and accept the terms of this agreement?` enter `Y` if so, and then press enter.
- `Please select your system type from the following list:` use `1` (Linux) then press enter.
- `Where do you want the library files [/usr/local/lib/ray]?` use `~/.local/lib/ray` -> press enter.

- `Do you want to change it?` -> `N` 
- You should see many `gcc` commands building the package on your home dir.
- Do the following to clean up:  
```bash
./makeall clean
```
- Check the installation:
```bash
Oconv
```
You should see:
```
#?RADIANCE
oconv
FORMAT=Radiance_octree
```
If so, optionally do:

```bash
cp -r doc/man/* ~/.local/share/man/
```
This adds the documentations for each command to DelftBlue home. So from this point on you'll be able to acces the docuementation of, say, `oconv` through: 
```bash
man oconv
``` 
and you you should see the command documentation and usage guide.

- Now, as was also hinted in the `README.txt`, ensure the environment variables are set. Do `vi ~/.bashrc`

- Ensure these variables exist, or put manually set them at the end of this file:
```
export MANPATH=~/.local/share/man:
export RAYPATH=~/.local/lib/ray:
```
(variable for `PATH` must be already present in this file at the top: `PATH="$HOME/.local/bin:$HOME/bin:$PATH"`)
            
Now you should have a fully functioning Radiance v6.0 on your DelftBlue account. Good luck with your simulations and research!
