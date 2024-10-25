import telebot
import os, random

bot = telebot.TeleBot("7799455501:AAHCBMi8D9yYSBQklG-ThnJ9FFalKmTcOT4")

# @bot.message_handler(commands=["mem"])
# def send_mem(message):
#    with open("images\81f63572-0ddb-4ba2-acde-9e2b8f52d389.jpeg", "rd") as f:
#       bot.send_photo(massage.chat.id, f)

@bot.message_handler(commands=["mem"])
def send_mem(message):
    img_name = random.choice(os.listdir("images"))
    with open(f"images/{img_name}", "rb") as function:

        bot.send_photo(message.chat.id, function)


@bot.message_handler(command=["start"])
def start_command(message):

    bot.send_message(message.chat.id, "Привет! Используй команду /mem, чтобы получить мем")

@bot.message_handler(command=["command"])
def command(message):
    fact_list = []

    bot.send_message(message.chat.id,random.choice(fact_list))

@bot.message_handler(commands=["fact"])
def fact_command(massage):
    bot.send_message(massage.chat.id, "Ежегодно в воды Мирового океана сбрасывается свыше 6 млрд. кг отходов, основную часть из которых составляет пластик.")


bot.polling()
