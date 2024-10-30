import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'You have logged in as {bot.user}')

@bot.command()
async def mem(ctx):
    with open('images/mem1.jpg', 'rb') as f:
        picture = discord.File(f)
    await ctx.send(file=picture)

@bot.command("saran")
async def saran_daur_ulang(ctx, item: str):
    # Daftar barang yang bisa didaur ulang
    daur_ulang = ['kertas', 'kardus', 'botol plastik', 'kaleng', 'kaca']
    
    # Jika item ada dalam daftar daur_ulang, beri saran untuk mendaur ulang
    if item.lower() in daur_ulang:
        await ctx.send(f"Baiklah! {item.capitalize()} sebaiknya didaur ulang.")
    else:
        await ctx.send(f"Baiklah! {item.capitalize()} bisa dibuang ke tempat sampah biasa.")

