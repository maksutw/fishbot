import telebot


TOKEN = '6934656716:AAFnGHxwLQXOtKrMMKGRBQIeQDAHCrptlMA'


bot = telebot.TeleBot(TOKEN)


@bot.message_handler(commands=['рыба'])
def show_fishing_spots(message):
   
    fishing_spots = {
        'окунь': 'Места обитания окуня в Беларуси: озера Нарочь, Свитязь, Острово, Черное.',
        'щука': 'Места обитания щуки в Беларуси: реки Западная Двина, Березина, Припять, Днепр.',
        'карп': 'Места обитания карпа в Беларуси: пруды и озера в Минском районе, озера Бездонное, \
                Дидово, Глубокое, Большое Протока.',
        'карась': 'Места обитания карася в Беларуси: пруды и озера в Витебской области, Березина, \
                река Волма, озеро Дригеляйское.'
    }

    
    command = message.text[6:].lower()

 
    if command in fishing_spots:
        bot.reply_to(message, fishing_spots[command])
    else:
        bot.reply_to(message, "К сожалению, информации о данной рыбе не найдено.")


bot.polling()
