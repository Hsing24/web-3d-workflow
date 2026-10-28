# 工具選擇與執行前提

## 選擇原則

優先選擇可由 Agent 呼叫、可讀取結果、可保存參數且能局部修改的工具。只選當前路線需要的能力，不預先安裝全部工具。

先確認實際版本與入口，再編寫依賴 API 的腳本。將可重複且已驗證的操作收成腳本；保留美術判斷與路線選擇的彈性。

## 能力與工具對應

| 能力 | 工具候選與介面 | 執行前需確認 |
| --- | --- | --- |
| 幾何建模與整合 | Blender Python、背景 CLI、Geometry Nodes；可選 Blender MCP | Blender 版本、操作 API、來源相容性、輸出位置與可回退副本 |
| 精準參數建模 | CadQuery、build123d 的 Python 介面 | 尺寸資料、曲面到網格的輸出、細分精度、組裝資訊 |
| 影像生成 3D | Meshy、Tripo、Rodin 等官方 API | 輸入與格式、模型版本、費用額度、輪詢與失敗處理、來源權利、下載保留期 |
| 自動重拓撲 | 服務端 remesh、Quad Remesher、Instant Meshes 等 | 實際可用 CLI／插件與授權、UV 和控制保留方式、是否符合動態需求 |
| 表面與烘焙 | Blender；有必要時加入 Substance 3D Painter 等 | 可否自動操作、來源／目標網格、UV、貼圖種類、色彩與輸出規格 |
| 掃描重建 | RealityScan 或其他攝影測量工具 | 照片品質與覆蓋、軟體版本與可操作介面、授權及尺度 |
| 網站資產整理 | glTF Transform、glTF Validator；可評估 gltfpack | 版本、輸出擴充、階層與動畫是否保留、載入器與解碼器支援 |
| 網站運行與檢查 | 既有引擎；Three.js、瀏覽器自動化與目標裝置量測 | 實際專案技術、材質與動畫支援、裝置測量能力 |

Blender MCP 是操作介面，skill 是決策與流程指引。已有背景 CLI 能完成的批次工作，可直接使用 CLI；需要互動場景觀察時，再依可用能力選 MCP。

## 能力檢查紀錄

在任務目錄記錄需要的工具是否可用、版本、呼叫入口、來源文件、已完成的小樣本及限制。清楚區分「文件支援」「本機可呼叫」「樣本驗證通過」。

對雲端服務，金鑰由安全的執行環境提供，不放入需求檔或腳本。確認已授權的使用額度；失敗重試需計入成本，任務成功後保存必要輸出和來源資訊。

生成、remesh、rigging 和動畫是不同能力，不能因服務支援其中一項就推定全部適用。對綁定尤其要確認角色類型、姿勢與輸出控制；例如 Meshy Rigging API 文件目前以標準人形角色為主要適用對象。

## 壓縮與呈現

GLB 是常用網站交付封裝，並非所有程序效果都必須產生模型檔。WebP 主要降低影像傳輸體積；KTX2 是容器，搭配 Basis Universal 與相容載入器可轉成裝置支援的 GPU 壓縮貼圖。實際視覺與效能需測試。

Meshopt、Draco、貼圖壓縮、量化及減面處理的是不同成本。不要預設每個資產都能以固定比例無損縮小，或套用某個面數就能保證幀率。程序著色同樣有計算、更新和像素覆蓋成本。

## 官方資料入口

下列入口作為查證起點；執行時依所選版本核對，不將範例參數當作永久契約。

- [Blender Geometry Nodes](https://docs.blender.org/manual/en/latest/modeling/geometry_nodes/introduction.html)
- [CadQuery](https://cadquery.readthedocs.io/en/latest/intro.html)
- [Meshy Image to 3D](https://docs.meshy.ai/en/api/image-to-3d)、[多圖輸入](https://docs.meshy.ai/en/api/multi-image-to-3d)、[Remesh](https://docs.meshy.ai/en/api/remesh)、[Rigging](https://docs.meshy.ai/en/api/rigging)
- [Tripo OpenAPI](https://docs.tripo3d.ai/)
- [RealityScan 貼圖重投射](https://rshelp.capturingreality.com/en-US/tools/reprojection.htm)
- [glTF Transform](https://gltf-transform.dev/cli)、[glTF Validator](https://github.com/KhronosGroup/glTF-Validator)
- [Three.js GLTFLoader](https://threejs.org/docs/pages/GLTFLoader)、[KTX2Loader](https://threejs.org/docs/pages/KTX2Loader.html)、[貼圖記憶體](https://threejs.org/manual/pages/textures.html)
