# s2-streaming

[Quickstart Reference Guide](https://s2.dev/docs/quickstart)

```bash
# Install homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo >> /home/ubuntu/.bashrc
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/ubuntu/.bashrc
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

```bash
# Install s2.
brew install s2-streamstore/s2/s2
```

```bash
# Set token.
s2 config set --auth-token BwwAAAAAAABnas1ZNfupXFkec64Th6Dv3U6gqD1rHwMTzXtv
```

```bash
# Create a basin
export MY_BASIN_NAME="exp-basin"
s2 create-basin $MY_BASIN_NAME
```

```bash
# List basins
s2 list-basins
```

```bash
# Create a stream.
s2 create-stream s2://$MY_BASIN_NAME/starwars
```

```bash
# Create a read session.
s2 read s2://$MY_BASIN_NAME/starwars -s 0 2> /dev/null
```

```bash
# Create an append session in another terminal.
export MY_BASIN_NAME="exp-basin" # Set the basin name for new terminal
nc towel.blinkenlights.nl 23 | s2 append s2://$MY_BASIN_NAME/starwars
```

```bash
# Test the latency
s2 create-stream s2://$MY_BASIN_NAME/ping -s express
s2 ping s2://$MY_BASIN_NAME/ping -n 10
```
