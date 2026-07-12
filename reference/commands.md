# Homelab Command Reference
Commands I use for routine Homelab maintenance, Docker management, monitoring, and troubleshooting.

# Update Server
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove -y
sudo reboot

## Check Upgradable 
apt list --upgradable

## Prune Docker Images
docker image prune -af

## Pihole 
sudo pihole -up
sudo pihole status

### Gravity
sudo pihole -g

## UFW Status
sudo ufw status verbose

## Tailscale Status
tailscale status


# Permissions 
sudo chown -R 1000:1000 /PATH
sudo chmod -R 775 /PATH

# Storage Check
df -h

# Memory Check
free -h


# Docker Status
docker ps

## Docker Restart
sudo systemctl restart docker

## Docker Compose
docker compose up -d
docker compose down
docker compose restart
docker compose config

# ClamAV Scan
clamscan -r -i <PATH>

## Container Logs
docker logs <container> --tail 50
docker logs -f <container>

# Github Push
git add .
git commit -m "[PUSH NAME]"
git push origin main

    

