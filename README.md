# btcprice

![screenshot](https://i.imgur.com/3jPwKR7.png)

## NOTE
I strongly suggest btcpricesh over btcprice since it's way faster, but currently it only supports usd as a report currency and has an osx dependency(uses a private api, for checking internnet speed)

### SPEED TESTS (btcpricesh v btcprice)
~~~~
# Download new data (this will vary depending on your internet speed)
btcpricesh
real    0m0.170s
user    0m0.054s
sys     0m0.036s

btcprice
real    0m0.205s
user    0m0.046s
sys     0m0.054s

# Load from cache
btcpricesh
real    0m0.029s
user    0m0.006s
sys     0m0.016s

btcprice
real    0m0.101s
user    0m0.040s
sys     0m0.055s
~~~~

## Install
~~~~shell
#### btcprice ####
wget https://raw.githubusercontent.com/kkristof200/btcprice/master/btcprice -O /usr/local/bin/btcprice && chmod u+x /usr/local/bin/btcprice
# or
curl https://raw.githubusercontent.com/kkristof200/btcprice/master/btcprice > /usr/local/bin/btcprice && chmod u+x /usr/local/bin/btcprice

#### btcpricesh ####
wget https://raw.githubusercontent.com/kkristof200/btcprice/master/btcpricesh -O /usr/local/bin/btcpricesh && chmod u+x /usr/local/bin/btcpricesh
# or
curl https://raw.githubusercontent.com/kkristof200/btcprice/master/btcpricesh > /usr/local/bin/btcpricesh && chmod u+x /usr/local/bin/btcpricesh
~~~~

## Usage
~~~~shell
btcprice -c ['USD', 'GBP' or 'EUR'] # defaults to 'USD'
btcpricesh
~~~~

## ADD TO POWERLEVEL10K AS PROMPT ELEMENT (what is shown at every command on the right side)
To set up iterm with p10k, follow this [tutorial](https://gist.github.com/kevin-smets/8568070)

Open iterm and run
~~~~shell
nano ~/.p10k.zsh
~~~~

Add btcprice to prompt elements
~~~~shell
typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
  ... other elments ...
  btcprice or btcpricesh
  ... other elments ...
)
~~~~

Add this function to the bottom
~~~~shell
function prompt_btcprice() {
  btcprice_str=$(btcprice)

  if [ "$btcprice_str" != "<ERROR>" ]; then
    p10k segment -f 208 -i '' -t $btcprice_str
  fi
}

or

function prompt_btcpricesh() {
  btcprice_str=$(btcpricesh)

  if [ "$btcprice_str" != "" ]; then
    p10k segment -f 208 -i '' -t $btcprice_str
  fi
}
~~~~
 - is the btc-icon font used from [nerd-fonts](https://github.com/ryanoasis/nerd-fonts). Either install it and add it to terminal/iterm or change the icon in the script above

Close editor and run
~~~~shell
source ~/.p10k.zsh
~~~~

## Dependencies
- python (for btcprice)
- osx (for btcpricesh)
