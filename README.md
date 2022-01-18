import vk_api, json
from vkbottle.bot import Bot, Message
import time

#pip install vk.api 
#pip install vkbottle

bot = Bot(token="1a9e8556600ea01c9899f855ba500802c9f3cda64dbb010d06b16affe686208bece08b54101b8cd3d6f9c")

def get_keyboard(buts):
	global get_but
	nb = []
	color = ''
	for i in range(len(buts)):
		nb.append([])
		for k in range(len(buts[i])):
			nb[i].append(None)
	for i in range(len(buts)):
		for k in range(len(buts[i])):
			text = buts[i][k][0]
			if buts[i][k][1] == 'p':
				color = 'positive'
			elif buts[i][k][1] == 'n':
				color = 'negative'
			nb[i][k] = {
                "action": {
                    "type": "text",
                    "payload": "{\"button\": \"" + "1" + "\"}",
                    "label": f"{text}"
                },
                "color": f"{color}"
            }
	first_keyboard = {
	    'one_time': True,
	    'buttons': nb
	    }
	first_keyboard = json.dumps(first_keyboard, ensure_ascii=False).encode('utf-8')
	first_keyboard = str(first_keyboard.decode('utf-8'))
	return first_keyboard

keyboard1 = get_keyboard(
	[
		[ ('10 раз all подряд! (Могут выебать)', 'p') ],
		[ ('5 раз all подряд! (Могут дать пизды)', 'p') ],
		[ ('Ауе (Пизды не дают!)', 'p') ]
	]
)
			


@bot.on.message(text="10 раз all подряд! (Могут выебать)")
async def hi_handler(message: Message):
    users_info = await bot.api.users.get(message.from_id)
    await message.answer("{}, сейчас все будет!".format(users_info[0].first_name))
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")

@bot.on.message(text="5 раз all подряд! (Могут дать пизды)")
async def hi_handler(message: Message):
    users_info = await bot.api.users.get(message.from_id)
    await message.answer("{}, сейчас все будет!".format(users_info[0].first_name))
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")
    time.sleep(1)
    await message.answer("@all Зашли быстро!")

@bot.on.message(text="Ауе (Пизды не дают!)")
async def hi_handler(message: Message):
    users_info = await bot.api.users.get(message.from_id)
    await message.answer("{}, Пошел нахуй, набери в дурку, пусть тебя заберут!".format(users_info[0].first_name))


bot.run_forever()
