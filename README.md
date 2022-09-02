# nftables
nftables tuzfal configuracio
# logikai felosztas
 Az input lanc altalaban nem tul bonyolult egy routeren
#
A csomagok celja alapjan 3 tovabbi chain-re osztom fel a forward-chain nevu lancomat:
- nft add chain inet filter-table forward2lan-chain
- nft add chain inet filter-table forward2dmz-chain
- nft add chain inet filter-table forward2internet-chain
