# Bash Cheatsheet

### System

Mount an ISO disc image to a given mount point.

``mount myiso.iso /media/iso/ -t iso9660 -o ro,loop=/dev/loop0``

Executes a command foo for every file in the current directory matching the file name pattern.

``find . -name '*.txt' | while read L; do foo "$L"; done`` or

``for i in `find . -name '*.txt'`; do foo "$i"; done``

Recursively removes all .svn folders from current directory.

``rm -rf `find . -type d -name .svn` ``

Recursively match patterns in file names and replace them using sed.

``for i in `find . -name '*.png'`; do newfile=$(echo $i | sed s/png/ppm/); convert $i $newfile; rm -f $i; done``

Recursively search for a string in a particular directory

``grep -r 'searchterm' /dir/to/search``

### Document Handling

GhostScript strings together an arbitrary number of PDF documents in the given order.

``gs -dNOPAUSE -sDEVICE=pdfwrite -sOUTPUTFILE=out.pdf -dBATCH in1.pdf in2.pdf in3.pdf``

GhostScript extracts a subset of pages from a PDF (here, page 2-4).

``gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER -dFirstPage=2 -dLastPage=4 -sOutputFile=out.pdf in.pdf``

### Easy stuff (just can’t keep it in mind!)

``rpm -qa`` : List of all installed packages (Fedora)

``tar xvzf file.tar.gz`` : Decompress and extract a .tar.gz

``lspci`` : Hardware info

``uname -r`` : Kernel in use (all: uname -a)

``yum whatprovides "*filename*"`` : Search repos for file names

### Image Processing

Resizes all JPEG images in the current directory to the given size and using the given image quality. ImageMagick preserves aspect ratio and the output images are stored in the subdirectory ‘output’.

``find . -iname "*.jpg" | xargs -l -i convert -resize 1024x1024 -quality 85 {} ./output/{}``

Crops the image input.ppm and stores the result in output.ppm. [W] and [H] is the new width and height, respectively. [X] and [Y] are the coordinates of the top left corner of the cropping region in source image coordinates.

``convert input.ppm -crop [W]x[H]+[X]+[Y] output.ppm``

### Bash Prompt

Under bash, you can set your prompt by changing the value of the PS1 environment variable. For system wide permanent usage put this into /etc/bashrc or into /home/[user]/.bashrc (or similar).

``export PS1='\[\e[0;33m\]\u\[\e[0;39m\]@\[\e[0;32m\]\h\[\e[0;39m\][\[\e[0;37m\]\w\[\e[0;39m\]]\n\$ '``
