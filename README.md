# Health-food-quiz
import random
from PIL import Image
import os

# คำถามและตัวเลือก
quiz_questions = [
    {
        "question": "เลือกอาหารที่ดีต่อสุขภาพที่สุด:",
        "options": ["A. สลัดผัก", "B. เค้กช็อกโกแลต", "C. เฟรนช์ฟราย", "D. พิซซ่า"],
        "answer": "A",
        "image": "salad.jpg"  # ภาพอาหารสลัดผัก
    },
    {
        "question": "เลือกอาหารที่ช่วยลดความเครียด:",
        "options": ["A. ผลไม้สด", "B. ขนมปังทอด", "C. ไอศกรีม", "D. กาแฟ"],
        "answer": "A",
        "image": "fruits.jpg"  # ภาพผลไม้สด
    },
    {
        "question": "เลือกอาหารที่มีประโยชน์ต่อการเสริมสร้างระบบภูมิคุ้มกัน:",
        "options": ["A. ไข่ต้ม", "B. ขนมหวาน", "C. เบคอน", "D. น้ำอัดลม"],
        "answer": "A",
        "image": "eggs.jpg"  # ภาพไข่ต้ม
    }
]

# ฟังก์ชันแสดงภาพ
def show_image(image_path):
    try:
        img = Image.open(image_path)
        img.show()
    except FileNotFoundError:
        print(f"ไม่พบภาพ {image_path}")

# ฟังก์ชันสุ่มคำถาม
def quiz_game():
    score = 0
    random.shuffle(quiz_questions)
    
    for q in quiz_questions:
        print("\n" + q["question"])
        for option in q["options"]:
            print(option)
        
        # แสดงภาพที่เกี่ยวข้อง
        show_image(q["image"])

        answer = input("พิมพ์ตัวเลือกที่ถูกต้อง (A, B, C หรือ D): ").strip().upper()
        
        if answer == q["answer"]:
            print("✅ ตอบถูกต้อง!")
            score += 1
        else:
            print(f"❌ คำตอบที่ถูกต้องคือ {q['answer']}")
    
    print(f"\nคะแนนของคุณ: {score}/{len(quiz_questions)}")

# เริ่มเกม
if __name__ == "__main__":
    quiz_game()
