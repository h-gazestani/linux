نولان:‌
nmcli con show -a
nmcli dev status

sudo nmcli connection modify network_uuid IPv4.address new_static_IP/24
sudo nmcli connection modify f02789f7-9d84-3870-ac06-8e4edbd1ecd9 IPv4.address 10.0.2.27/24

sudo nmcli connection modify 'Wired connection 1' IPv4.address 10.0.2.27/24
sudo nmcli connection modify 'Wired connection 1' IPv4.gateway 10.0.2.11
sudo nmcli connection modify 'Wired connection 1' IPv4.dns 8.8.8.8
sudo nmcli connection modify 'Wired connection 1' IPv4.method manual
sudo nmcli connection down 'Wired connection 1.'
sudo nmcli connection up 'Wired connection 1.'
