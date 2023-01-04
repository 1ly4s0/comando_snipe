![Node build](https://github.com/eritislami/evobot/actions/workflows/node.yml/badge.svg)

![logo](https://cdn.discordapp.com/attachments/933698201486237716/947555143795228682/Diseno_sin_titulo_22.png)

# 🤖 Tutorial Discord Bot (TECNO BROS)
> Código del bot del tutorial de TECNO BROS, el vídeo es [este](https://www.youtube.com/watch?v=U-jNIYV2vBU)
## Requisitos

1. Tener un bot de Discord creado **[Guía](https://www.youtube.com/watch?v=qXev2kf-q_0)**
2. Tener Discord.js V12 o Discord.js V13 **[Guía](https://www.youtube.com/watch?v=qXev2kf-q_0)**
3. Tener el bot hosteado o en tu PC **[Guía](https://www.youtube.com/watch?v=0MkVTtLoMiI)**  
4.1 **(Opcional)** Tener el bot en algun host **[Guía](https://www.youtube.com/watch?v=0MkVTtLoMiI)**

## 🚀 Código de SNIPE

```js

const snipe = new Discord.Collection();
const snipe_user = new Discord.Collection();
const snipe_avatar = new Discord.Collection();
const snipe_archivos = new Discord.Collection();
const snipe_timestamp = new Discord.Collection();

client.on("messageDelete", async message => {
    if(message.author.bot) return;
    if(message.channel.type === "DM") return;

    const attachment = message.attachments.first() ? message.attachments.first().proxyURL : null;

    snipe.set(message.channel.id, message.content)
    snipe_user.set(message.channel.id, message.author.id)
    snipe_avatar.set(message.channel.id, message.author.displayAvatarURL({ dynamic: true }))
    snipe_archivos.set(message.channel.id, attachment)
    snipe_timestamp.set(message.channel.id, message.createdTimestamp)
})
```

## 🚀 Comando de SNIPE
```js

client.on("messageCreate", async message => {
    if(message.content.startsWith("tb!snipe")) {

        if(!snipe.get(message.channel.id)) return message.channel.send("No hay mensajes eliminados recientemente")

        const Embed = new Discord.MessageEmbed()
        .setTitle("Snipe")
        .setDescription(`**Mensaje eliminado:** ${snipe.get(message.channel.id)} \n **Autor:** ${client.users.cache.get(snipe_user.get(message.channel.id)).tag} \n **Eliminado hace:** <t:${Math.floor(snipe_timestamp.get(message.channel.id) / 1000)}:R>`)
        .setAuthor(client.users.cache.get(snipe_user.get(message.channel.id)).tag, snipe_avatar.get(message.channel.id))
        .setImage(snipe_archivos.get(message.channel.id))
        .setColor("BLURPLE")

        message.channel.send({ embeds: [Embed] })

    }
})
```
Después de modificar o añadir algo al código, recuerda o reiniciar tu bot o usar el comando `node index.js` para que los cambios se apliquen.

## ⚙️ Uso:

## SNIPE
![logo](https://cdn.discordapp.com/attachments/933698201486237716/1060244083899121704/image.png)




## 📝 Créditos
* [DISCORD](https://discord.gg/tecnobros)
* [YOUTUBE](https://youtube.com/tecnobros)

Copyright © **1ly4s0#2477** - 2023
