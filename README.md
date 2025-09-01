# computer-graphics
本專案是在 Processing/Java 架構下實作的小型繪圖程式。
依作業規範，不使用內建繪圖原語（line/circle/ellipse/bezier/rect/beginShape/vertex），僅以像素級方法完成各工具。

✅ 已完成功能
Line：Bresenham 直線演算法（整數運算）
Circle：Midpoint Circle（中點畫圓，八向對稱）
Ellipse：Midpoint Ellipse（中點畫橢圓，分區域 1/2）
Curve：三次 Bézier（De Casteljau 取樣）＋以 CGLine 連段
Polygon：多邊形外框（以 CGLine 串接頂點並自動封閉）
Pencil：自由手畫筆（連續取樣點用 CGLine 相連）
Eraser：框選擦除（像素覆蓋背景色；亦提供 pixels[] 直接改寫版本）
Clear：清空畫布
Undo：Z / Shift+Z 撤銷最後一個 Shape（依你實作）


🧩 專案結構（重點檔案）
HW1.pde：主程式（setup/draw、按鈕初始化、事件派送）

Renderer.pde：各工具互動流程（收集滑鼠點、呼叫 util 演算法）

LineRenderer / CircleRenderer / EllipseRenderer / CurveRenderer / PolygonRenderer / PencilRenderer / EraserRenderer
util.pde：核心繪圖演算法
CGLine(x1,y1,x2,y2)
CGCircle(cx,cy,r)
CGEllipse(cx,cy,r1,r2)
CGCurve(p1,p2,p3,p4)
CGEraser(p1,p2)
CGPolyline(verts, closed) / CGPolygon(verts)
drawPoint(x,y,color)（像素級畫點，或包 pixels[]）

Button.pde / ButtonFunction.pde / ShapeButton.pde：UI 控制
Point.pde / Vector3.pde / Shape 相關：資料結構、圖形基類

🖱️ 使用說明
工具列（左→右）
Line | Circle | Polygon | Ellipse | Curve | Pencil | Eraser | Clear
共通：請在畫布框（box）內操作，框外點擊無效。
Line：左鍵第一次選起點、第二次選終點完成；右鍵取消。
Circle：左鍵依序點「圓心 → 半徑點」完成；右鍵取消。
Ellipse：左鍵依序點「中心 → 設定水平半徑 → 設定垂直半徑」完成；右鍵取消。
Curve（Bézier）：左鍵依序點 4 點（起點、控制點1、控制點2、終點）完成；右鍵取消。
Polygon：左鍵逐點新增頂點，右鍵收邊（自動封閉）完成。
Pencil：按住左鍵拖曳；放開即生成一條由 CGLine 串接的折線。
Eraser：左鍵點一下在游標處以當下尺寸框選擦除；滑鼠滾輪可調大小（預設 4–30）。
Clear：清空所有形狀。
Undo：按 Z 撤銷上一個形狀。
