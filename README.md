GIF-RGB565-Converter
A web-based tool for converting animated GIF files to RGB565 format (.h and .bin files) optimized for embedded devices like ESP32 or LilyGo displays. This tool runs entirely in the browser using Pyodide (Python in WebAssembly) and Pillow for image processing—no server required!
Features

Client-Side Processing: Upload GIFs directly in your browser; no data leaves your device.
Animated GIF Support: Handles multi-frame GIFs with proper disposal methods (e.g., restore to background, do not dispose) and transparency.
Device Presets: Quick selection for common displays like LilyGo T-Display (240x135), LilyGo T-Display S3 (320x170), and ESP32-CYD (240x320).
Custom Dimensions: Manually set max width/height for scaling.
Output Formats:
.h file: Arduino-compatible header with PROGMEM arrays and frame delays.
.bin file: Binary metadata (frame count, dimensions, delays) + pixel data for direct firmware embedding.


RGB565 Conversion: Efficient 16-bit color format for low-memory MCUs.
Responsive UI: Modern, mobile-friendly design with status updates.




Feature
Description



Input
GIF files (animated, multi-frame)


Output
.h (C header) and .bin (binary)


Scaling
BICUBIC resampling for quality


Transparency
Handled via RGBA conversion with black background fallback


Frame Delays
Preserved from original GIF (default 100ms)


Demo
Check out the live demo on GitHub Pages.
Quick Start

Clone the Repository:
git clone https://github.com/LtcShadow/GIF-RGB565-Converter.git
cd GIF-RGB565-Converter


Open in Browser:

Open index.html in any modern browser (Chrome, Firefox, Safari recommended).
No installation needed—Pyodide loads dynamically via CDN.


Usage Steps:

Upload a GIF file.
Select a device preset or enter custom max width/height (e.g., 240x135).
Click "Convert and Generate Files".
Download the .h or .bin file once processing completes.



Example:

Input: A 100x100 pixel animated GIF with 10 frames.
Output: Scaled to 240x135, RGB565 pixels in PROGMEM array for Arduino or binary data for firmware.

Dependencies
This tool uses browser-based libraries loaded via CDN:



Library
Version
License
Purpose



Pyodide
v0.26.1
MPL 2.0
Runs Python in WebAssembly


Pillow
Latest (via micropip)
HDF5
Image processing (GIF parsing, resizing, RGB565 conversion)



Note: No npm/yarn/pip installs required. All processing is client-side.

Building and Customization

Edit the Code: Modify index.html for UI changes or the Python logic in the <script> tag.
Test Locally: Use a local server (e.g., python -m http.server) to avoid CORS issues with file uploads.
Deploy to GitHub Pages:
Go to repo settings > Pages.
Set Source to "Deploy from a branch" (main branch, /root).
Save and wait for the site to build (URL: https://ltcshadow.github.io/GIF-RGB565-Converter/).



Contributing
Contributions are welcome! To contribute:

Fork the repository.
Create a feature branch (git checkout -b feature/amazing-feature).
Commit your changes (git commit -m 'Add amazing feature').
Push to the branch (git push origin feature/amazing-feature).
Open a Pull Request.

Please ensure contributions are licensed under the MIT License. See CONTRIBUTING.md for more details (create this file if needed).
License
This project is licensed under the MIT License - see the LICENSE file for details.
Disclaimer

Copyright Responsibility: Users must ensure uploaded GIF files do not infringe copyrights. This tool processes files locally and does not store or distribute content. The developer is not liable for any illegal use.
Hardware Mentions: Device names (e.g., LilyGo T-Display, ESP32-CYD) are used for technical reference only and are not affiliated with any brand.
No Warranty: Provided "AS IS" per MIT License.

Acknowledgments

Developed in collaboration with Grok by xAI—thanks for the code generation and debugging assistance!
Inspired by embedded graphics tools in the Arduino/ESP32 community.

Troubleshooting



Issue
Solution



"Loading environment..." stuck
Ensure browser supports WebAssembly (update Chrome/Firefox). Check console for Pyodide errors.


Single-frame GIF error
Tool requires animated GIFs (multi-frame). Use tools like GIMP to create animations.


Transparency issues (e.g., 0x3186 pixels)
Code forces unexpected colors to black; edit Python color_to_rgb565 if needed.


Large GIF slow
Resize GIF beforehand (e.g., via online tools) or increase browser memory.


Download fails
Check file permissions; try in incognito mode.


If issues persist, open an Issue on GitHub.


GIF-RGB565-Converter
一個基於網頁的工具，用於將動態 GIF 檔案轉換為 RGB565 格式（.h 和 .bin 檔案），專為嵌入式裝置（如 ESP32 或 LilyGo 顯示器）優化。此工具完全在瀏覽器中運行，使用 Pyodide（WebAssembly 中的 Python）和 Pillow 進行圖像處理—無需伺服器！
功能特點

客戶端處理：直接在瀏覽器中上傳 GIF，資料不會離開您的裝置。
動態 GIF 支援：處理多幀 GIF，包括適當的 disposal 方法（例如還原至背景、不清除）和透明度。
裝置預設：快速選擇常見顯示器，如 LilyGo T-Display (240x135)、LilyGo T-Display S3 (320x170) 和 ESP32-CYD (240x320)。
自訂尺寸：手動設定最大寬高以進行縮放。
輸出格式：
.h 檔案：相容 Arduino 的標頭檔，包含 PROGMEM 陣列和幀延遲。
.bin 檔案：二進位中繼資料（幀數、尺寸、延遲）+ 像素資料，用於直接嵌入韌體。


RGB565 轉換：高效的 16 位元顏色格式，適合低記憶體 MCU。
響應式 UI：現代化、行動裝置友善的設計，包含狀態更新。




功能
描述



輸入
GIF 檔案（動態、多幀）


輸出
.h（C 標頭檔）和 .bin（二進位）


縮放
BICUBIC 重新取樣以確保品質


透明度
透過 RGBA 轉換處理，使用黑色背景作為後備


幀延遲
保留原始 GIF 的延遲（預設 100ms）


示範
請查看 GitHub Pages 的即時示範：https://ltcshadow.github.io/GIF-RGB565-Converter/。
快速入門

複製儲存庫：
git clone https://github.com/LtcShadow/GIF-RGB565-Converter.git
cd GIF-RGB565-Converter


在瀏覽器中開啟：

在任何現代瀏覽器中開啟 index.html（建議使用 Chrome、Firefox 或 Safari）。
無需安裝—Pyodide 會透過 CDN 動態載入。


使用步驟：

上傳 GIF 檔案。
選擇裝置預設或輸入自訂最大寬高（例如 240x135）。
點擊「轉換並產生檔案」。
處理完成後，下載 .h 或 .bin 檔案。



範例：

輸入：100x100 像素的動態 GIF，含 10 幀。
輸出：縮放至 240x135，RGB565 像素置於 Arduino 的 PROGMEM 陣列或二進位資料。

依賴項目
此工具使用透過 CDN 載入的瀏覽器程式庫：



程式庫
版本
授權
用途



Pyodide
v0.26.1
MPL 2.0
在 WebAssembly 中運行 Python


Pillow
最新版（透過 micropip）
HDF5
圖像處理（GIF 解析、縮放、RGB565 轉換）



注意：無需 npm/yarn/pip 安裝。所有處理皆在客戶端進行。

建置與自訂

編輯程式碼：修改 index.html 以變更 UI 或 <script> 標籤中的 Python 邏輯。
本機測試：使用本機伺服器（例如 python -m http.server）以避免檔案上傳的 CORS 問題。
部署至 GitHub Pages：
進入儲存庫設定 > Pages。
設定來源為「從分支部署」（main 分支，/root）。
儲存並等待網站建置（URL：https://ltcshadow.github.io/GIF-RGB565-Converter/）。



貢獻指南
歡迎貢獻！請遵循以下步驟：

Fork 此儲存庫。
建立功能分支（git checkout -b feature/amazing-feature）。
提交變更（git commit -m 'Add amazing feature'）。
推送
