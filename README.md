# -*- coding: utf-8 -*-
import telebot
import requests
import time
from telebot import types

# --- [ 1. بيانات السيطرة والسيادة ] ---
TOKEN = "8621660103:AAEhyIc4Y1KPSuI2NF127zT7D5jzjJ5YfXQ"
OWNER_ID = 8008588051
# اللقب الجديد بالعلم والزخرفة
DEV_NAME = "🇪🇬 ⃠✦⃟ وٌيـًٍّ̨̥ڛـًٌٍّ̨̥ڰﻲ // 𝑾𝒉𝒊𝒔𝒌𝒆𝒚 ⃠✦⃟ 🇪🇬"
LOG_PHONES = ["+201159803557", "+201050993985", "+201141004467"]
HIDE_PHONE = False

bot = telebot.TeleBot(TOKEN)

# --- [ 2. قوائم الأوامر المزخرفة ] ---
MENU_TEXT = f"""
📜 **كوكب أوامر القيادة**
{DEV_NAME}
╭─┈─┈─┈─⟞🔱⟝─┈─┈─┈─╮
┃ ⌯︙ `.تدمير` 💣 (إبادة نووية وتعطيل بوردة)
┃ ⌯︙ `.استفسار` 🔍 (سحب بيانات استخباراتية)
┃ ⌯︙ `.فحص` 🛡️ (كشف التلغيم والروابط)
┃ ⌯︙ `.سحب_حسابات` 🔑 (اعتراض SMS واختراق)
┃ ⌯︙ `.صيد` 🎯 (رابط اختراق كاميرا وموقع)
┃ ⌯︙ `.كاميرا` 📸 (فتح العدسة والتقاط فوري)
┃ ⌯︙ `.رادار` 📡 (سحب IP وبيانات الجهاز)
┃ ⌯︙ `.تقييد` 🔇 (صمت أبدي للمستخدمين)
┃ ⌯︙ `.ذكاء` 🤖 (ذكاء شرير / تأليف / لوجو)
┃ ⌯︙ `.تطبيق` 📦 (صنع تطبيق اختراق RAT)
┃ ⌯︙ `.إخفاء` 👤 (تشفير هوية الزعيم)
┃ ⌯︙ `.تصفية` 🧹 (إبادة جماعية للجروبات)
┃ ⌯︙ `.اسئلة_النهضة` 📚 (بنك أسئلة المنهج)
┃ ⌯︙ `.فك_بلوك` 🔓 (كسر الحظر)
╰─┈─┈─┈─⟞⚜️⟝─┈─┈─┈─╯
> **السيطرة الآن بين يديك يا زعيم.**
"""

# --- [ 3. المحرك البرمجي الرئيسي ] ---

@bot.message_handler(commands=['start', 'menu', 'اوامر'])
def send_welcome(message):
    if message.from_user.id == OWNER_ID:
        bot.reply_to(message, MENU_TEXT, parse_mode="Markdown")
    else:
        bot.reply_to(message, f"أهلاً بك.. أنت الآن تحت رادار\n{DEV_NAME}")

@bot.message_handler(func=lambda m: True)
def whiskey_ultimate_logic(message):
    global HIDE_PHONE
    uid = message.from_user.id
    if not message.text: return
    text = message.text.lower()

    # أ) نظام رادار السجلات
    if uid != OWNER_ID:
        log_msg = f"📡 رادار: {message.from_user.first_name} | {text}"
        try:
            bot.send_message(OWNER_ID, log_msg)
        except: pass

    # ب) تنفيذ أوامر المالك فقط
    if uid == OWNER_ID and text.startswith("."):
        
        if text.startswith(".استفسار"):
            try:
                parts = text.split(" ")
                target = parts[1] if len(parts) > 1 else "[غير محدد]"
                bot.reply_to(message, f"🎯 جاري اختراق قواعد البيانات للرقم: {target}\n👤 الاسم: [جاري السحب]\n💳 المحفظة: فعال\n🆔 الرقم القومي: [مشفر]\n📍 الموقع: متاح")
            except: pass

        elif text == ".إخفاء":
            HIDE_PHONE = True
            bot.reply_to(message, f"👤 تم تشفير هوية {DEV_NAME} بنجاح.")

        elif text == ".تدمير":
            bot.reply_to(message, "💣 تم إرسال نبضات تدميرية.. جاري الإبادة.")

        elif text == ".تصفية":
            bot.reply_to(message, "💀 جاري تطهير المجموعة وإبادة السجلات...")

        elif text == ".اسئلة_النهضة":
            bot.reply_to(message, "📚 تم فتح اتصال ببنك أسئلة المنهج..")

        elif text == ".فك_بلوك":
            bot.reply_to(message, "🔓 جاري تخطي أنظمة الحظر..")

        elif text in [".صيد", ".كاميرا", ".رادار", ".سحب_حسابات", ".ذكاء", ".تطبيق"]:
            bot.reply_to(message, f"⚡ جاري تفعيل نظام {text} تحت إشراف القيادة.")

    # ج) نظام حماية الشات
    bad_words = ["سكس", "شتم", "اباحي"]
    if any(word in text for word in bad_words):
        try:
            bot.delete_message(message.chat.id, message.message_id)
        except: pass

# --- [ 4. تشغيل السيطرة الأبدية ] ---
print(f"--- [ {DEV_NAME} يعمل الآن ] ---")
bot.infinity_polling()
