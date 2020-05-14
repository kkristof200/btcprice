# btcprice

![screenshot](https://i.imgur.com/3jPwKR7.png)

## NOTE
I strongly suggest btcpricesh over btcprice since it's way faster (pure shell > python), but currently it only supports usd as an output

### SPEED TESTS (btcprice v btcpricesh)
~~~~
# Download new data
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
# btcprice
cd /usr/local/bin && wget https://raw.githubusercontent.com/kkristof200/btcprice/master/btcprice && chmod u+x btcprice
# btcpricesh
brew install jq
cd /usr/local/bin && wget https://raw.githubusercontent.com/kkristof200/btcprice/master/btcpricesh && chmod u+x btcpricesh
~~~~

## Usage
~~~~shell
btcprice -c ['USD', 'GBP' or 'EUR'] # defaults to 'USD'
btcpricesh
~~~~

## ADD TO POWERLEVEL10K AS PROMPT ELEMENT
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
