# btcprice

![screenshot](https://i.imgur.com/3jPwKR7.png)

## Install
~~~~shell
cd /usr/local/bin && wget https://raw.githubusercontent.com/kkristof200/btcprice/master/btcprice && chmod u+x btcprice
~~~~

## Usage
~~~~shell
btcprice
~~~~

## ADD TO POWERLEVEL10K AS PROMPT ELEMENT
Open iterm and run
~~~~shell
nano ~/.p10k.zsh
~~~~

Add bday to prompt elements
~~~~shell
typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
  ... other elments ...
  btcprice
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
~~~~
 - is the btc-icon font used from [nerd-fonts](https://github.com/ryanoasis/nerd-fonts). Either install it and add it to terminal/iterm or change the icon in the script above

Close editor and run
~~~~shell
source ~/.p10k.zsh
~~~~

## Dependencies
python
