# nftables
nftables tuzfal configuracio
# logikai felosztas
a csomagok celja alapjan 3 tovabbi chain-re osztom fel a forward lancomat:
- nft add chain inet filter-table forward2lan-chain
- nft add chain inet filter-table forward2dmz-chain
- nft add chain inet filter-table forward2internet-chain
