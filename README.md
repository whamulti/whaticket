## Access Data

User: admin@whaticket.com
Password: admin

## Upgrading

WhaTicket is a working in progress and we are adding new features frequently. To update your old installation and get all the new features, you can use a bash script like this:

**Note**: Always check the .env.example and adjust your .env file before upgrading, since some new variable may be added.

```bash
nano updateWhaticket
```

```bash
#!/bin/bash
echo "Updating Whaticket, please wait."

git reset --hard
git pull
cd backend
npm install
rm -rf dist
npm run build
npx sequelize db:migrate
npx sequelize db:seed
cd ../frontend
npm install
rm -rf build
npm run build
pm2 restart all

echo "Update finished. Enjoy!"
```

Make it executable and run it:

```bash
sudo chmod +x updateWhaticket

sudo ./updateWhaticket

```

```bash
chmod +x updateWhatsapp-web
./updateWhatsapp-web
```