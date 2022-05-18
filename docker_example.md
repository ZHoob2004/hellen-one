This is an example docker build process using https://github.com/rusefi/alphax-2chan


1. Clone hellen-one repo and build docker image

```
git clone https://github.com/andreika-git/hellen-one
cd hellen-one
docker build -t hellen-one .
```

2. Clone target repo and cd into it

```
git clone https://github.com/rusefi/alphax-2chan
cd alphax-2chan
```

3. Use your new docker image to run `hellen-one/bin/copy_from_Kicad.py`

```
docker run --rm -it --entrypoint python3 -v "$(pwd)":/${PWD##*/} hellen-one ./bin/copy_from_Kicad.py "frames:alphax_" "//${PWD##*/}" "../../gerber" "2ch" "c"
```

4. Use the same image to run `hellen-one/bin/create_board_with_prefix.sh`

```
docker run --rm -it --entrypoint bash -v "$(pwd)":/${PWD##*/} hellen-one ./bin/create_board_with_prefix.sh "alphax_" "/alphax-2chan" "2ch" "c" "bom_replace_alphax-2ch-c.csv " "0,4"
```
