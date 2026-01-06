# HANDOVER - Cổ Học Tinh Hoa

> File này dùng để tiếp tục dự án. Chỉ cần nói: "Đọc file HANDOVER.md và tiếp tục dự án"

## Tổng quan dự án

**Tên:** Cổ Học Tinh Hoa (Ancient Wisdom)
**Mô tả:** Ứng dụng web về văn hóa tâm linh và chiêm tinh học phương Đông
**GitHub:** https://github.com/nclamvn/co-hoc-tinh-hoa
**Tech:** React 18 + Vite + Tailwind CSS + Framer Motion

## Trạng thái hiện tại

### Đã hoàn thành
- [x] Trang chủ với Hero section
- [x] Navigation với mega menu dropdown
- [x] Trang Tử Vi (AstrologyPage) - nhập ngày sinh, tính Mệnh Cung
- [x] Trang Thần Số Học (NumerologyPage) - tính Life Path, Expression, Soul Urge, Personality, Birthday
- [x] Trang Lịch Vạn Niên (LunarCalendarPage) - đầy đủ tính năng
- [x] Database kiến giải Thần Số Học (src/data/numerologyMeanings/)
- [x] Database kiến giải Tử Vi (src/data/tuViMeanings/)
- [x] Dịch tiếng Trung → Việt cho festivals, activities, spirits trong lịch
- [x] Responsive layout

### Cấu trúc file quan trọng

```
src/
├── pages/
│   ├── HomePage.jsx
│   ├── AstrologyPage.jsx      # Tử Vi
│   ├── NumerologyPage.jsx     # Thần Số Học
│   ├── LunarCalendarPage.jsx  # Lịch Vạn Niên
│   ├── PalmistryPage.jsx      # Xem Tướng Tay
│   └── PhysiognomyPage.jsx    # Xem Tướng Mặt
│
├── data/
│   ├── numerologyMeanings/
│   │   ├── index.js           # Export tất cả
│   │   ├── lifePathMeaning.js # Số Chủ Đạo (1-9, 11, 22)
│   │   ├── expressionMeaning.js
│   │   ├── soulUrgeMeaning.js
│   │   ├── personalityMeaning.js
│   │   ├── birthdayMeaning.js
│   │   └── cyclesMeaning.js   # Pinnacles & Challenges
│   │
│   └── tuViMeanings/
│       ├── index.js
│       ├── cungMeaning.js     # 12 Cung
│       └── chinhTinhMeaning.js # 14 Chính Tinh
│
├── utils/
│   └── lunarCalendar/
│       └── lunarEngine.js     # Engine tính âm lịch + dịch tiếng Việt
│
├── components/
│   ├── navigation/Navigation.jsx
│   └── lunarCalendar/
│       ├── DayCard.jsx
│       ├── TodayWidget.jsx
│       ├── MonthCalendar.jsx
│       └── DayDetailModal.jsx
│
└── App.jsx                    # Router chính
```

### Navigation IDs (dùng trong App.jsx)

```javascript
// Dịch vụ
'astrology'     → AstrologyPage
'numerology'    → NumerologyPage
'palmistry'     → PalmistryPage
'physiognomy'   → PhysiognomyPage

// Công cụ
'lunar-calendar'  → LunarCalendarPage
'auspicious-date' → (chưa làm)
'compatibility'   → (chưa làm)

// Premium
'premium'           → PremiumPage
'premium-numerology'→ (chưa làm)
'report'            → (chưa làm)
```

## Các vấn đề đã fix

1. **Import path numerologyMeanings** - phải dùng `/index` explicit
2. **Syntax error lifePathMeaning.js** - array ending với `}` thay vì `]`
3. **React object render error** - check `typeof meaning.overview`
4. **Dropdown bị cắt** - thêm `alignRight` prop cho Premium dropdown
5. **DayCard bị cắt viewport** - thêm responsive CSS, `max-width: 100%`
6. **Tiếng Trung trong lịch** - thêm FESTIVAL_TRANSLATIONS, ACTIVITY_TRANSLATIONS trong lunarEngine.js

## Environment Variables

```bash
# .env (không commit)
VITE_OPENAI_API_KEY=your_key_here
```

## Commands

```bash
npm run dev      # Development
npm run build    # Production build
npm run preview  # Preview build
```

## TODO - Việc có thể làm tiếp

### Ưu tiên cao
- [ ] Trang Xem Ngày Tốt (auspicious-date)
- [ ] Trang Xem Hợp Tuổi (compatibility)
- [ ] Hoàn thiện Premium features

### Ưu tiên trung bình
- [ ] Thêm AI analysis với OpenAI
- [ ] Trang Xem Tướng Tay chi tiết
- [ ] Trang Xem Tướng Mặt chi tiết
- [ ] Export PDF báo cáo

### Cải thiện
- [ ] Code splitting để giảm bundle size
- [ ] PWA support
- [ ] Dark/Light mode toggle
- [ ] Lưu lịch sử tra cứu (localStorage)

## Lưu ý quan trọng

1. **lunar-javascript** library trả về tiếng Trung, đã được dịch trong `lunarEngine.js`
2. **Vite** environment variables phải có prefix `VITE_`
3. **SPA routing** trên Render cần file `public/_redirects`
4. **API key** đã được gitignore, an toàn để share public

## Cách tiếp tục

1. Đọc file này
2. Chạy `npm run dev` để xem trạng thái hiện tại
3. Chọn task từ TODO list hoặc yêu cầu tính năng mới
4. Khi xong, chạy `npm run build` để test production

---
*Cập nhật lần cuối: 2026-01-06*
