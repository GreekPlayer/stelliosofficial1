const {Client, Intents, MessageReaction} = require("discord.js")
const allIntents = new Intents(32767);
const client = new Client({ intents: allIntents });
const { Collection } = require('discord.js');
const db = require('quick.db')
const Invites = new Collection();
const moment = require('moment');
const fs = require('fs');
const usersMap = new Map();
const prefix = '!';
const { MessageEmbed } = require('discord.js');
const { MessageActionRow, MessageSelectMenu, MessageButton } = require ("discord.js")
const ms = require('ms')
const Discord = require('discord.js')
const axios = require('axios')
const { channel } = require('diagnostics_channel');
const { set } = require('express/lib/application');
const voiceCollection = new Collection();
const { AuditLogEvent } = require('discord.js');
const { syncBuiltinESMExports } = require("module");
const osu = require('node-os-utils');
var os = require('os');
const { ActionRowBuilder, Modal, TextInputBuilder, TextInputStyle, TextInputComponent } = require('discord.js');
client.commands = new Collection();
client.login("MTI3OTQyMDgzMjg3NTI4NjU3OQ.GCU_x9.NAWOvy-K8ioruDMMwZyyxcp5IX7CMDS_t8SGAg")
////// Start Up \\\\\\
client.once('ready', () => {
  console.log(`${client.user.tag} is online`);
  client.user.setPresence(
    { 
        activities: [
            { 
                name: 'Silence Roleplay' , 
                type: "PLAYING" 
            }
        ], 
        status: "dnd" // online, idle, invisible, dnd
    }
) 
});
//Errors
client.on('shardError', error => {
    console.error('A websocket connection encountered an error:', error);
    })
    
    process.on('unhandledRejection', error => {
    console.error(error);
    });
////////////////////////
    const config = {

      "ticketrole": "1159913451003588738",
      "ticketlogs": "1166735573256523959",

      "color": "BLUE",
      "name": "Silence Roleplay",
      "logo": "https://cdn.discordapp.com/attachments/1135605584121577513/1160219736416714752/image.png?ex=654652d5&is=6533ddd5&hm=4183113b62b1ae8c2eb8a0810ec2e5bda6b7c38732ac6f0f5adcde04fcbee669&",
      "prefix": "!",


    "appmodal_logs": "1166735595473752135",
    "e1": "Όνομα",
    "e2": "Ηλικία",
    "e3": "Steam Name",
    "e4": "Πόσες ώρες έχετε στο FiveM",
    "e5": "Γιατί να επιλέξουμε εσένα",

    "joinlogs": "1166735128630935572",
    "autorole": "1166401137679806554",
    "leavelogs": "1166735128630935572",
    "msglogs": "1166735181407862814",
    "voicelogs": "1166735207764865194",
    "rolelogs": "1166735242242048091",
    "channellogs": "1166735287121104976",
    "kicklogs": "1166735308138762321",
    "banlogs": "1166735355513417768",


    "MEMBERS": "1166734657082114088",
    "BOOSTS": "1166734713122201660",
    "id": "1159913144945234073",

    "anti_link_logs": "1162414614483574784",
    "suggestion": "1162414572137873408"




    }
// !IP \\
    client.on('messageCreate', message => {
      if(!message.guild) return;
      
        if(message.content === '!ip') {
      if(!message.member.permissions.has("ADMINISTRATOR")) return;
      message.delete()
      const embed = new MessageEmbed()
        .setDescription(`**Ip: Coming Soon... **`)
        .setColor(config.color)
      message.channel.send({embeds:[embed]})
        }
      })

/////////////////////////////////////////////////////////////
//Ticket System
client.on('messageCreate', message => {
    if (message.content.toLowerCase() === '!ticket') {
          if (!message.member.permissions.has("ADMINISTRATOR")) {
        message.delete()
      }  
      else {
        message.delete()
      const embed = new MessageEmbed()
        .setAuthor(config.name,config.logo)
        .setDescription(`**Για την άμεση εξυπηρέτηση σας μπορείτε να ανοίξετε ένα ticket πατοντας το <:ezgif:1166736415208521839> ώστε να μιλήσετε με κάποιον ανώτερο και να λύσετε το πρόβλημα σας.**`)
      .setTitle(``)
  .setThumbnail(config.logo)
  .setColor(config.color);
      const ticketopen = new MessageButton()
        .setStyle('SECONDARY')
        .setLabel('')
        .setEmoji('<:ezgif:1166736415208521839> ')
        .setCustomId('ticket_open');
      const row = new MessageActionRow()
        .addComponents(ticketopen)
  
      message.channel.send({embeds: [embed], components: [row]})
    }
  }
  })
  ////////////////////////////////////////////////////////////////
  client.on('interactionCreate', async interaction => {
  if (!interaction.isButton()) return;
    if (interaction.customId === 'ticket_open') {
      const embed = new MessageEmbed()
        .setTitle("Ticket Limit")
        .setDescription("**You already have a Ticket open.**")
        .setColor(config.color)
      const limembe = new MessageEmbed()
        .setTitle("🛡️Ticket Limit🛡️")
        .setColor(config.color)
        .setDescription(`${interaction.user} has already a ticket opened.`)
      
      if (client.guilds.cache.get(interaction.guildId).channels.cache.find(c => c.topic == interaction.user.id)) {
        return interaction.reply({
          embeds: [embed],
          ephemeral: true
        }),
        client.channels.cache.get(config.ticketlogs).send({embeds: [limembe]})
  
  
    } 
      interaction.guild.channels.create(`🎫ticket-${interaction.user.username}`, {
        parent: interaction.channel.parent,
        topic: interaction.user.id,
        permissionOverwrites: [{
            id: interaction.user.id,
            allow: ['VIEW_CHANNEL'],
            deny: ['SEND_MESSAGES'],
          },
          {
            id: interaction.guild.roles.everyone,
            deny: ['VIEW_CHANNEL'],
          },
          {
            id: config.ticketrole,
            allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
          },
        ],
        type: 'GUILD_TEXT',
      }).catch(()=>{}).then(async c => {
interaction.reply({content: `**✅ | ${c}**`,ephemeral:true})
        const embed = new MessageEmbed()
        .setAuthor(config.name,config.logo)
        .setColor(config.color)
        .setDescription("**Προσδιορίστε το θέμα στο οποίο ανήκει το πρόβλημά σας.**")
        .setThumbnail(config.logo)
        const row = new MessageActionRow()
          .addComponents(
            new MessageSelectMenu()
            .setCustomId("category")
            .setPlaceholder("Click here to set the Ticket topic.")
            .addOptions([{
                label: 'Ban Appeal',
                value: '⛔Ban Appeal',
                emoji: '⛔',
              },
              {
                label: 'Donate',
                value: '💸Donate',
                emoji: '💸',
              },
  
              {
                label: 'Staff Report',
                value: '⚠Staff Report',
                emoji: '⚠',
              },
              {
                label: 'Support',
                value: '📞Support',
                emoji: '📞',
              },
  
              {
                label: 'Cancel Ticket',
                value: 'cancel_ticket',
                description: 'To cancel your Ticket.',
                emoji: '⛔',
              },
            ]),
          );
        
        msg = await c.send({embeds: [embed], components: [row]}).catch(()=>{})
        msg = await c.send({
          content: `<@!${interaction.user.id}>`,
        }).then(msg  => {
          msg.delete().catch(()=>{})
        })
       
        
        
        })
        
    }
  })
  client.on('interactionCreate', async interaction => {
    if (!interaction.isSelectMenu())return;


////

        if (interaction.values[0] === '⛔Ban Appeal') {
  
  interaction.reply({ ephemeral: true}).catch(() => { })
  interaction.channel.bulkDelete(5)
  interaction.channel.permissionOverwrites.set([
    {
      id: interaction.user.id,
      allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
    },
    {
        id: config.ticketrole,
        allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
      },
    {
      id: interaction.guild.roles.everyone,
      deny: ['VIEW_CHANNEL'],
    },
  ])
  interaction.channel.setName(`${interaction.values}-${interaction.user.username}`)
  const embed = new MessageEmbed()
    .setDescription(`**Περίγραψε παρακάτω τι θα ήθελες για να σε εξυπηρετήσει κάποιος ανώτερος το συντομότερο δυνατόν.**`)
    .setFooter('To close the Ticket press "🔒Close"')
    .setColor(config.color)
    .setAuthor(interaction.user.tag+" ● "+interaction.values, interaction.user.displayAvatarURL())
    const closebutton = new MessageButton()
    .setStyle('SECONDARY')
    .setLabel('\🔒Close')
    .setCustomId('ticket_close');
    const row = new MessageActionRow()
      .addComponents(closebutton)
  interaction.channel.send({embeds: [embed], components: [row]})
  const log_embed = new MessageEmbed()
  .setTitle("🔨Ticket Creation🔨")
  
  .setDescription("ㅤ\n⚬ Opened From :  <@!"+interaction.channel.topic+">\n\n⚬ Topic : "+interaction.values+"\n\n⚬ Channel : <#"+interaction.channel.id+">")
  .setColor(config.color)
  client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
        }
//
if (interaction.values[0] === '💸Donate') {
  
    interaction.reply({ ephemeral: true}).catch(() => { })
    interaction.channel.bulkDelete(5)
    interaction.channel.permissionOverwrites.set([
      {
        id: interaction.user.id,
        allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
      },
      {
          id: config.ticketrole,
          allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
        },
      {
        id: interaction.guild.roles.everyone,
        deny: ['VIEW_CHANNEL'],
      },
    ])
    interaction.channel.setName(`${interaction.values}-${interaction.user.username}`)
    const embed = new MessageEmbed()
      .setDescription(`**Περίγραψε παρακάτω τι θα ήθελες για να σε εξυπηρετήσει κάποιος ανώτερος το συντομότερο δυνατόν.**`)
      .setFooter('To close the Ticket press "🔒Close"')
      .setColor(config.color)
      .setAuthor(interaction.user.tag+" ● "+interaction.values, interaction.user.displayAvatarURL())
      const closebutton = new MessageButton()
      .setStyle('SECONDARY')
      .setLabel('\🔒Close')
      .setCustomId('ticket_close');
      const row = new MessageActionRow()
        .addComponents(closebutton)
    interaction.channel.send({embeds: [embed], components: [row]})
    const log_embed = new MessageEmbed()
    .setTitle("🔨Ticket Creation🔨")
    
    .setDescription("ㅤ\n⚬ Opened From :  <@!"+interaction.channel.topic+">\n\n⚬ Topic : "+interaction.values+"\n\n⚬ Channel : <#"+interaction.channel.id+">")
    .setColor(config.color)
    client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
          }
//
if (interaction.values[0] === '📦Replace') {
  
    interaction.reply({ ephemeral: true}).catch(() => { })
    interaction.channel.bulkDelete(5)
    interaction.channel.permissionOverwrites.set([
      {
        id: interaction.user.id,
        allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
      },
      {
          id: config.ticketrole,
          allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
        },
      {
        id: interaction.guild.roles.everyone,
        deny: ['VIEW_CHANNEL'],
      },
    ])
    interaction.channel.setName(`${interaction.values}-${interaction.user.username}`)
    const embed = new MessageEmbed()
      .setDescription(`**Περίγραψε παρακάτω τι θα ήθελες για να σε εξυπηρετήσει κάποιος ανώτερος το συντομότερο δυνατόν.**`)
      .setFooter('To close the Ticket press "🔒Close"')
      .setColor(config.color)
      .setAuthor(interaction.user.tag+" ● "+interaction.values, interaction.user.displayAvatarURL())
      const closebutton = new MessageButton()
      .setStyle('SECONDARY')
      .setLabel('\🔒Close')
      .setCustomId('ticket_close');
      const row = new MessageActionRow()
        .addComponents(closebutton)
    interaction.channel.send({embeds: [embed], components: [row]})
    const log_embed = new MessageEmbed()
    .setTitle("🔨Ticket Creation🔨")
    
    .setDescription("ㅤ\n⚬ Opened From :  <@!"+interaction.channel.topic+">\n\n⚬ Topic : "+interaction.values+"\n\n⚬ Channel : <#"+interaction.channel.id+">")
    .setColor(config.color)
    client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
          }
          //
          if (interaction.values[0] === '⚠Staff Report') {
  
            interaction.reply({ ephemeral: true}).catch(() => { })
            interaction.channel.bulkDelete(5)
            interaction.channel.permissionOverwrites.set([
              {
                id: interaction.user.id,
                allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
              },
              {
                  id: config.ticketrole,
                  allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
                },
              {
                id: interaction.guild.roles.everyone,
                deny: ['VIEW_CHANNEL'],
              },
            ])
            interaction.channel.setName(`${interaction.values}-${interaction.user.username}`)
            const embed = new MessageEmbed()
              .setDescription(`**Περίγραψε παρακάτω τι θα ήθελες για να σε εξυπηρετήσει κάποιος ανώτερος το συντομότερο δυνατόν.**`)
              .setFooter('To close the Ticket press "🔒Close"')
              .setColor(config.color)
              .setAuthor(interaction.user.tag+" ● "+interaction.values, interaction.user.displayAvatarURL())
              const closebutton = new MessageButton()
              .setStyle('SECONDARY')
              .setLabel('\🔒Close')
              .setCustomId('ticket_close');
              const row = new MessageActionRow()
                .addComponents(closebutton)
            interaction.channel.send({embeds: [embed], components: [row]})
            const log_embed = new MessageEmbed()
            .setTitle("🔨Ticket Creation🔨")
            
            .setDescription("ㅤ\n⚬ Opened From :  <@!"+interaction.channel.topic+">\n\n⚬ Topic : "+interaction.values+"\n\n⚬ Channel : <#"+interaction.channel.id+">")
            .setColor(config.color)
            client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
                  }
                  //
                  if (interaction.values[0] === '📞Support') {
  
                    interaction.reply({ ephemeral: true}).catch(() => { })
                    interaction.channel.bulkDelete(5)
                    interaction.channel.permissionOverwrites.set([
                      {
                        id: interaction.user.id,
                        allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
                      },
                      {
                          id: config.ticketrole,
                          allow: ['SEND_MESSAGES', 'VIEW_CHANNEL'],
                        },
                      {
                        id: interaction.guild.roles.everyone,
                        deny: ['VIEW_CHANNEL'],
                      },
                    ])
                    interaction.channel.setName(`${interaction.values}-${interaction.user.username}`)
                    const embed = new MessageEmbed()
                      .setDescription(`**Περίγραψε παρακάτω τι θα ήθελες για να σε εξυπηρετήσει κάποιος ανώτερος το συντομότερο δυνατόν.**`)
                      .setFooter('To close the Ticket press "🔒Close"')
                      .setColor(config.color)
                      .setAuthor(interaction.user.tag+" ● "+interaction.values, interaction.user.displayAvatarURL())
                      const closebutton = new MessageButton()
                      .setStyle('SECONDARY')
                      .setLabel('\🔒Close')
                      .setCustomId('ticket_close');
                      const row = new MessageActionRow()
                        .addComponents(closebutton)
                    interaction.channel.send({embeds: [embed], components: [row]})
                    const log_embed = new MessageEmbed()
                    .setTitle("🔨Ticket Creation🔨")
                    
                    .setDescription("ㅤ\n⚬ Opened From :  <@!"+interaction.channel.topic+">\n\n⚬ Topic : "+interaction.values+"\n\n⚬ Channel : <#"+interaction.channel.id+">")
                    .setColor(config.color)
                    client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
                          }
 /////////////////////////////


                                if (interaction.values[0] === 'cancel_ticket') {
  
                                  interaction.reply({ ephemeral: true}).catch(() => { })
                                  
                                  const log_embed = new MessageEmbed()
                                  .setTitle("⛔Ticket Cancellation⛔")
                                  
                                  .setDescription("ㅤ\n⚬ Opened From : <@!"+interaction.channel.topic+">\n\n⚬ Canceled From : "+`${interaction.member}`)
                                  .setColor(config.color)
                                  client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
                                  interaction.channel.delete()
                                        }
  //telos apo values    
      })
  //ticket close
  client.on('interactionCreate', async interaction => {
    if (!interaction.isButton()) return;
      if (interaction.customId === 'ticket_close') {
        interaction.reply({ ephemeral: true}).catch(() => { })
        const aksiologisi_embed = new MessageEmbed()
        .setAuthor(config.name,config.logo)
        .setDescription(`**Rate our service**`)
        .setThumbnail(config.logo)
        .setColor(config.color)
        const row = new MessageActionRow()
        .addComponents(
          new MessageSelectMenu()
          .setCustomId("category")
          .setPlaceholder("Click here to close the Ticket.")
          .addOptions([{
              label: '⭐',
              value: '⭐',
            },
            {
              label: '⭐⭐',
              value: '⭐⭐',
            },
            {
              label: '⭐⭐⭐',
              value: '⭐⭐⭐',
            },

          ]),
        );
        interaction.channel.send({embeds: [aksiologisi_embed], components: [row]})
        }
  
      })
  //telos
    
  //
  client.on('interactionCreate', async interaction => {
    if (!interaction.isSelectMenu())return;
        if (interaction.values[0] === '⭐') {
          interaction.reply({ ephemeral: true}).catch(() => { })
          const log_embed = new MessageEmbed()
          .setTitle("✅Close Ticket✅")
          
          .setDescription(`ㅤ\n⚬ Opened From : <@!${interaction.channel.topic}>\n\n⚬ Closed From : <@!${interaction.user.id}>\n\n⚬ Rate : ⭐`)
          .setColor(config.color)
          client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
          interaction.channel.delete().catch(() => { })
        }
        if (interaction.values[0] === '⭐⭐') {
          interaction.reply({ ephemeral: true}).catch(() => { })
          const log_embed = new MessageEmbed()
          .setTitle("✅Close Ticket✅")
          
          .setDescription(`ㅤ\n⚬ Opened From : <@!${interaction.channel.topic}>\n\n⚬ Closed From : <@!${interaction.user.id}>\n\n⚬ Rate : ⭐⭐`)
          .setColor(config.color)
          client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
          interaction.channel.delete().catch(() => { })
        }
        if (interaction.values[0] === '⭐⭐⭐') {
          interaction.reply({ ephemeral: true}).catch(() => { })
          const log_embed = new MessageEmbed()
          .setTitle("✅Close Ticket✅")
          
          .setDescription(`ㅤ\n⚬ Opened From : <@!${interaction.channel.topic}>\n\n⚬ Closed From : <@!${interaction.user.id}>\n\n⚬ Rate : ⭐⭐⭐`)
          .setColor(config.color)
          client.channels.cache.get(config.ticketlogs).send({embeds: [log_embed]})
          interaction.channel.delete().catch(() => { })
        }
     })
     //Applications
     client.on('messageCreate', message => {
      if(!message.guild) return;
        if (message.content.toLowerCase() === '!app') {
              if (!message.member.permissions.has("ADMINISTRATOR")) {
            message.delete()
          }
          else {
              message.delete()
            const embed = new MessageEmbed()
              .setAuthor(config.name,config.logo)
              .setDescription(`**Καλώς ήρθες στον ${message.guild.name}. Για να ενταχθείς στο __Staff Team__™, πάτησε το παρακάτω Βutton, εκεί συμπλήρωσε την φόρμα.**`)
        .setThumbnail(config.logo)
        .setColor(config.color);
            const ticketopen = new MessageButton()
              .setStyle('SECONDARY')
              .setLabel('💼')
              .setCustomId('apptmodal');
            const row = new MessageActionRow()
              .addComponents(ticketopen)
            message.channel.send({embeds: [embed], components: [row]})
          }
        }
        }) 
///////////
client.on('interactionCreate', async (interaction) => {
  if (interaction.isButton()) {
    if (interaction.customId === 'apptmodal') {
      const modal = new Modal()
        .setCustomId('app_modal')
        .setTitle(`Application | ${interaction.user.username}`)
        .addComponents([
          new MessageActionRow().addComponents(
              new TextInputComponent()
                .setCustomId('appmodal_input_1')
                .setLabel(config.e1)
                .setStyle('PARAGRAPH')
                .setMinLength(1)
                .setMaxLength(200)
                .setPlaceholder('Γράψε την απάντηση σου εδώ')
                .setRequired(true),
            ),
            ///////
            new MessageActionRow().addComponents(
              new TextInputComponent()
                .setCustomId('appmodal_input_2')
                .setLabel(config.e2)
                .setStyle('PARAGRAPH')
                .setMinLength(1)
                .setMaxLength(200)
                .setPlaceholder('Γράψε την απάντηση σου εδώ')
                .setRequired(true),
            ),
  ///////////
  new MessageActionRow().addComponents(
    new TextInputComponent()
      .setCustomId('appmodal_input_3')
      .setLabel(config.e3)
      .setStyle('PARAGRAPH')
      .setMinLength(1)
      .setMaxLength(200)
      .setPlaceholder('Γράψε την απάντηση σου εδώ')
      .setRequired(true),
  ),
  ///////////
  new MessageActionRow().addComponents(
    new TextInputComponent()
      .setCustomId('appmodal_input_4')
      .setLabel(config.e4)
      .setStyle('PARAGRAPH')
      .setMinLength(1)
      .setMaxLength(200)
      .setPlaceholder('Γράψε την απάντηση σου εδώ')
      .setRequired(true),
  ),
  ///////////
  new MessageActionRow().addComponents(
    new TextInputComponent()
      .setCustomId('appmodal_input_5')
      .setLabel(config.e5)
      .setStyle('PARAGRAPH')
      .setMinLength(1)
      .setMaxLength(200)
      .setPlaceholder('Γράψε την απάντηση σου εδώ')
      .setRequired(true),
  ),

        ]);

      await interaction.showModal(modal);
    }
  }

  if (interaction.isModalSubmit()) {
    if (interaction.customId === 'app_modal') {
      const response1 = interaction.fields.getTextInputValue('appmodal_input_1')
      const response2 = interaction.fields.getTextInputValue('appmodal_input_2')
      const response3 = interaction.fields.getTextInputValue('appmodal_input_3')
      const response4 = interaction.fields.getTextInputValue('appmodal_input_4')
      const response5 = interaction.fields.getTextInputValue('appmodal_input_5')
      const embed2 = new MessageEmbed()
      .setAuthor(config.name,config.logo)
      .setColor('GREEN')
      .setDescription("**Το Application σου στάλθηκε.**")
      interaction.reply({embeds: [embed2], ephemeral: true})


          const embed = new MessageEmbed()
          
          .addFields(
            { name: `Application From:`, value: `**${interaction.member} | ${interaction.user.username} | \`\`${interaction.user.id}\`\`**`, inline: true},
            { name: `${config.e1}`, value: `\`${response1}\``, inline: false},
            { name: `${config.e2}`, value: `\`${response2}\``, inline: false},
            { name: `${config.e3}`, value: `\`${response3}\``, inline: false},
            { name: `${config.e4}`, value: `\`${response4}\``, inline: false},
            { name: `${config.e5}`, value: `\`${response5}\``, inline: false},
          )
          .setColor(config.color)
          .setTimestamp()
          .setAuthor(interaction.user.tag, interaction.user.displayAvatarURL({ size: 1024, dynamic: true }))
            client.channels.cache.get(config.appmodal_logs).send({embeds: [embed]})


          }}
        })
///Join-Left Logs
client.on('guildMemberAdd', (member) => {
  const user = member.user
  const channelID = member.guild.channels.cache.get(config.joinlogs)
  const guild = member.guild.id 
  const memberEmbed = new MessageEmbed()
  .setAuthor( member.user.username, member.user.displayAvatarURL(), "https://discord.com/users/" + member.user.id)
  .setDescription(` \`\`\` Join \`\`\` \n**Register**: \`${moment(member.user.createdAt).format("MMM Do YYYY").toLocaleString()}\`\n**Mention:** <@!${member.user.id}>`)
    .setColor('GREEN')
      const role = member.guild.roles.cache.get(config.autorole)//auto role
      member.roles.add(role).catch(() => { })
      channelID.send({embeds: [memberEmbed] })
  })
  client.on('guildMemberRemove', (member) => {
  const monitorID = member.guild.channels.cache.get(config.leavelogs)//left logs
  const guild = member.guild.id 
  const memberEmbed = new MessageEmbed()
    .setColor('RED')
    .setDescription(` \`\`\` Leave \`\`\` \n**Register**: \`${moment(member.user.createdAt).format("MMM Do YYYY").toLocaleString()}\`\n**Mention:** <@!${member.user.id}>`)
    .setAuthor( member.user.username, member.user.displayAvatarURL(), "https://discord.com/users/" + member.user.id)
    .setImage('')
      monitorID.send({embeds: [memberEmbed] })
  })
////// Message Edit Logs \\\\\\
client.on("messageUpdate", async (oldMessage, newMessage) => {
  try{
if(newMessage.author.bot) return
let channel = oldMessage.guild.channels.cache.get(config.msglogs)
const url = oldMessage.url
const embed = new MessageEmbed()
.setTitle(`Edited Message Logs`)
.setColor('#993366')
.setTimestamp()
.setURL(url)
.addField(`Παλιο μυνημα`, `*${oldMessage.content}*`, false)
.addField(`Τελικο μυνημα`, `*${newMessage.content}*`, false)
.addField(`Το μυνημα ειναι του`, `**<@${oldMessage.author.id}>**`, true)
.addField(`Καναλι που ηταν το μυνημα`, `**<#${oldMessage.channel.id}>**`, true)
channel.send({embeds: [embed] }).catch(()=>{})
  }catch{
      
  }
})
var temporary = [];

////// Message Delete \\\\\\
client.on('messageDelete', async message => {
    if (!message.guild) return;
    const fetchedLogs = await message.guild.fetchAuditLogs({
        limit: 1,
        type: 'MESSAGE_DELETE',
    });
    const deletionLog = fetchedLogs.entries.first();
    const embed = new MessageEmbed({
      "author": {
        "name": message.author.tag,
        "url": "https://discord.com/users/" + message.author.id ,
        "icon_url": message.author.displayAvatarURL()
      },
      "color": 15483204,
      "description": "​\n" + message.content + "\n\n**Mention: <@" + message.author.id + ">\nΚανάλι: <#" + message.channel.id + ">**"
    })
    if (!deletionLog) return     client.channels.cache.get(config.msglogs).send({embeds: [embed] })

    const { executor, target } = deletionLog;
    const embed2 = new MessageEmbed({
      "author": {
        "name": message.author.tag,
        "url": "https://discord.com/users/" + message.author.id,
        "icon_url": message.author.displayAvatarURL()
      },
      "color": 15483204,
      "description": "​\n" + message.content + "\n\n**Mention: <@" + message.author.id + ">\nΚανάλι: <#" + message.channel.id + ">**\n**Από τον/ην: <@" + executor.id + ">**"
    })
    const embed3 = new MessageEmbed({
      "author": {
        "name": message.author.tag,
        "url": "https://discord.com/users/" + message.author.id ,
        "icon_url": message.author.displayAvatarURL()
      },
      "color": 15483204,
      "description": "​\n" + message.content + "\n\n**Mention: <@" + message.author.id + ">\nΚανάλι: <#" + message.channel.id + ">**"
    })
  try{
    if (target.id == message.author.id) {
    client.channels.cache.get(config.msglogs).send({embeds: [embed2] }).catch(()=>{})
    } else {
    client.channels.cache.get(config.msglogs).send({embeds: [embed3] }).catch(()=>{})
    }
}catch{
  
}
});

//voice logs
var temporary = [];
client.on('voiceStateUpdate', (oldMember, newMember) => {
let newUserChannel = newMember.channelId;
let oldUserChannel = oldMember.channelId;


try{
  if(newUserChannel){
  const voicelogs = newMember.guild.channels.cache.get(config.voicelogs)
  const voicee = new MessageEmbed({
    "author": {
      "name": newMember.member.user.tag,
      "url": "https://discord.com/users/" + newMember.member.user.id,
      "icon_url": newMember.member.user.displayAvatarURL()
    },
    "color": 4371328,
    "description": "**Κανάλι: <#" + newUserChannel + "> • " + newMember.channel.name + "\nMention: <@" + newMember.member.user.id + ">**"
  })
  voicelogs.send({ embeds: [voicee] })
  }

  else{
    if(oldUserChannel){
      const voicelogs = oldMember.guild.channels.cache.get(config.voicelogs)
      const voice = new MessageEmbed({
        "author": {
          "name": newMember.member.user.tag,
          "url": "https://discord.com/users/" + newMember.member.user.id,
          "icon_url": newMember.member.user.displayAvatarURL()
        },
        "color": 15681608,
        "description": "**Κανάλι: <#" + oldUserChannel + "> • `" + oldMember.channel.name + "`\nMention: <@" + oldMember.member.user.id + ">**"
      })
      voicelogs.send({ embeds: [voice] })
    }
}
}catch{
e => console.log(e.message)
}
})





////// Role Create-Delete Logs \\\\\\
client.on("roleCreate", async (role) => {
  const fetchedLogs = await role.guild.fetchAuditLogs({
        limit: 1,
        type: 'ROLE_CREATE',
    });

  const fasdfa = fetchedLogs.entries.first();
    let { executor, target, reason } = fasdfa;
  if(executor === null) executor = "\u200B";
  if(target === null) target = "\u200B";
  if(reason === null) reason = "\u200B";

    const embed = new MessageEmbed()
      .setColor("GREEN")
      .setAuthor(executor.username, executor.displayAvatarURL(), `https://discord.com/users/${executor.id}`)
      .setDescription("A new role was created!")
      .addFields(
        {name: "User", value: executor.username},
        {name: "Role Name", value: target.name},
        {name: "Role ID", value: target.id},
        {name: "reason", value: reason}
      )
      // .setFooter(`Role ID: ${id}`)
      .setTimestamp();

      client.channels.cache.get(config.rolelogs).send({embeds: [embed] }).catch(() => { })
      })
client.on("roleDelete", async (role) => {

  const fetchedLogs = await role.guild.fetchAuditLogs({
        limit: 1,
        type: 'ROLE_DELETE',
    });

  const fasdfa = await fetchedLogs.entries.first();
    let { executor, target, reason, a } = fasdfa;
  if(executor === null) executor = "\u200B";
  if(target === null || target === undefined) target = "\u200B";
  if(reason === null) reason = "\u200B";

    const embed = new MessageEmbed()
      .setColor("RED")
      .setAuthor(executor.username, executor.displayAvatarURL(), `https://discord.com/users/${executor.id}`)
      .setDescription("A new role was Deleted!")
      .addFields(
        {name: "User", value: executor.username},
        {name: "Role Name", value: role.name},
        {name: "Role ID", value: role.id},
        {name: "reason", value: reason}
      )
      // .setFooter(`Role ID: ${id}`)
      .setTimestamp();

      client.channels.cache.get(config.rolelogs).send({embeds: [embed] })

});
//role update
client.on('guildMemberUpdate', async function(oldMember, newMember) {
  const log = await newMember.guild.fetchAuditLogs({ limit: 1, type: 'MEMBER_ROLE_UPDATE' }).then(logs => logs.entries.first());
  let addedRoles = newMember.roles.cache.filter(role => !oldMember.roles.cache.has(role.id));
  let removedRoles = oldMember.roles.cache.filter(role => !newMember.roles.cache.has(role.id));

  if (removedRoles.size > 0) {
    const removeRoleEmbed = new MessageEmbed()
      .setColor('RED')
      .setAuthor(`${oldMember.user.tag}`, oldMember.user.avatarURL())
      .setDescription(`Ο/Η <@!${oldMember.id}> έχασε τον ρόλο <@&${removedRoles.map(r => r.id)}> από τον/την <@!${log.executor.id}>`)
      .setTimestamp()
      .setFooter(`ID : ${oldMember.id}`)
    client.channels.cache.get(config.rolelogs).send({embeds: [removeRoleEmbed] })
  }

  if (addedRoles.size > 0) {
    const addRoleEmbed = new MessageEmbed()
      .setColor('GREEN')
      .setAuthor(`${oldMember.user.tag}`, oldMember.user.avatarURL())
      .setDescription(`Ο/Η <@!${oldMember.id}> πήρε τον ρόλο <@&${addedRoles.map(r => r.id)}> από τον/την <@!${log.executor.id}>`)
      .setTimestamp()
      .setFooter(`ID : ${oldMember.id}`)
    client.channels.cache.get(config.rolelogs).send({embeds: [addRoleEmbed] })
  }
});
//channel create
client.on("channelCreate", async function(channel) {
  const logs = await channel.guild.fetchAuditLogs({ limit: 1, type: 'CHANNEL_CREATE' });
  const log = logs.entries.first();
  if (!log) return;
  const embed = new MessageEmbed()
    .setTitle("Channel Created")
    .setColor("GREEN")
    .setDescription(`Από τον/την : <@!${log.executor.id}>\nΚανάλι : <#${channel.id}>\nΕίδος : ${channel.type}\nΌνομα : ` + channel.name)
    .setTimestamp()
    .setFooter("ID :" + channel)
  client.channels.cache.get(config.channellogs).send({embeds: [embed] })
});
//channel delete
client.on("channelDelete", async function(channel) {
  const logs = await channel.guild.fetchAuditLogs({ limit: 1, type: 'CHANNEL_DELETE' });
  const log = logs.entries.first();
  if (!log) return;
  const embed = new MessageEmbed()
    .setTitle("Channel Deleted")
    .setColor("RED")
    .setDescription(`Από τον/την : <@!${log.executor.id}>\nΚανάλι : <#${channel.id}>\nΕίδος : ${channel.type}\nΌνομα : ` + channel.name)
    .setTimestamp()
    .setFooter("ID :" + channel)
  client.channels.cache.get(config.channellogs).send({embeds: [embed] })
});
//kick 
client.on('guildMemberRemove', async member => {
  const logs = await member.guild.fetchAuditLogs({ limit: 1, type: 'MEMBER_KICK' });
  const log = logs.entries.first();
  const { reason } = log;
  
  if (!log) return;
  const embed = new MessageEmbed()
    .setColor("RED")
    .setDescription(`${member.user} **kicked**\n\nΑπό τον/την : ${log.executor}\nΛόγος : ${reason}`)
  if (Date.now() - log.createdTimestamp < 5000) {
    client.channels.cache.get(config.kicklogs).send({embeds: [embed] })
  
  }})
//ban logs
client.on('guildBanAdd', async ban => {
const logs = await ban.guild.fetchAuditLogs({ limit: 1, type: 'MEMBER_BAN_ADD' });
const log = logs.entries.first();
const { reason } = log;
if (!log) return;
const embed = new MessageEmbed()
  .setColor("RED")
  .setDescription(`${ban.user} **banned**\n\nΑπό τον/την : ${log.executor}\nΛόγος : ${reason}`)
if (Date.now() - log.createdTimestamp < 5000) {
  client.channels.cache.get(config.banlogs).send({embeds: [embed] })
}})
//unban logs
client.on('guildBanRemove', async member => {
    const logs = await member.guild.fetchAuditLogs({ limit: 1, type: 'MEMBER_BAN_REMOVE' });
    const log = logs.entries.first();
    const { reason } = log;
    if (!log) return;
    const embed = new MessageEmbed()
      .setColor("RED")
      .setDescription(`${member.user} **unbanned**\n\nΑπό τον/την : ${log.executor}`)
    if (Date.now() - log.createdTimestamp < 5000) {
      client.channels.cache.get(config.banlogs).send({embeds: [embed] })
    
    
}})


//Server Stats
client.on("ready", function(){
  if(config.MEMBERS){
      const member = client.guilds.cache.get(config.id).channels.cache.get(config.MEMBERS)
      if(member){
          setInterval(() => {
              member.setName(`👤Members: ${client.guilds.cache.get(config.id).members.cache.filter(member => !member.user.bot).size}`).catch(() => { })  
          }, 5 * 60 * 1000);
      }
  }
  if(config.BOOSTS){
      const boost = client.guilds.cache.get(config.id).channels.cache.get(config.BOOSTS)
      if(boost){
          setInterval(() => {
              boost.setName(`🔮・Boosts: ${client.guilds.cache.get(config.id).premiumSubscriptionCount}`).catch(() => { })  
          }, 5 * 60 * 1000);
      } 
  }

})

//Anti Link System\\
client.on("messageCreate", async message =>{

  if(message.content.includes("discord.gg/") || message.content.includes("discord.io/") || message.content.includes("youtube.com/") || message.content.includes("https://") || message.content.includes("twitch.tv/") || message.content.includes("discord.com/")){
        if (message.member.permissions.has('ADMINISTRATOR'))return
        
        message.delete().catch(()=>{})
        message.member.send("**Δεν μπορείς να στείλεις Link**").catch(()=>{})
            const logs = message.guild.channels.cache.get(config.anti_link_logs)
            if(logs){
                const embed = new MessageEmbed()
                .setTitle("**Anti Links System**")
                .setDescription("**Ο/Η <@!"+message.member.user.id+"> ("+message.member.user.username+") πρόσπαθησε να στείλει link!\n\nLink : **||"+message.content+"||")
                .setFooter("Αναγνωριστικό ("+message.member.user.id+")")
                .setColor(config.color)
                logs.send({embeds: [embed] })
            }}})
          // Dm all \\

 /// purge/ clear///
 client.on('messageCreate', async(message) => {
  if(!message.guild) return;
    if (message.author.bot)return
    const args = message.content.slice(prefix.length).trim().split(/ +/g);
    const command = args.shift().toLowerCase();
        if(message.content.startsWith('!purge') || message.content.startsWith('!clear')){
          if(!message.member.permissions.has("ADMINISTRATOR")) return message.reply("**You do not have permissions.**")
                const content = args.join(' ');
                if(!content) return message.channel.send("How many messages do you want to delete ?")
                message.channel.bulkDelete(content).catch(e => {message.channel.send('You can not delete so old messages.')})
  
        }
    }) 
//lock & unlock command
client.on("messageCreate", async message =>{
  if(!message.guild) return;
    
      if (message.content === '!lock'){
        if (message.member.permissions.has("ADMINISTRATOR")){
        message.channel.send({content: "Channel Locked"})
        message.delete()
        message.channel.permissionOverwrites.set([
          {
            id: message.guild.id,
            deny: ['SEND_MESSAGES']
          },
      ])
    
    }}})  
    client.on("messageCreate", async message =>{
  if(!message.guild) return;
    
  
        if (message.content === '!unlock'){
          if (message.member.permissions.has("ADMINISTRATOR")){
              message.delete()
        message.channel.send({content: "Channel unlocked"})
        message.channel.permissionOverwrites.set([
          {
            id: message.guild.id,
            allow: ['SEND_MESSAGES']
          },
      ])
      }}})

///!say2 command
client.on('messageCreate', async(message) => {
  if(!message.guild) return;
    if (message.author.bot)return
    const args = message.content.slice(prefix.length).trim().split(/ +/g);
    const command = args.shift().toLowerCase();
    if(command === 'say2'){
          if(!message.member.permissions.has("ADMINISTRATOR")) return;
                const content = args.join(' ');
                const embed = new MessageEmbed()
                  .setColor(config.color)
                  .setThumbnail(config.logo)
                  .setAuthor(config.name,config.logo)
                  .setDescription(content);
                  message.channel.send({embeds: [embed]});
                message.delete({timeout: 1500}).catch(err => console.log(err));
        }
    })
//DMALL
client.on("messageCreate", message => {

  if (message.content.startsWith(prefix + 'dmall')) {
    message.delete
    args = message.content.split(" ").slice(1);
    var argresult = args.join(' ');

    message.guild.members.cache.forEach(member => {
      member.send(argresult).then(console.log(`[+] ${member.user.username}#${member.user.discriminator}`)).catch(e => console.error(`[-] ${member.user.username}#${member.user.discriminator}`));
    })
    console.log(`✅`)

  }

})
