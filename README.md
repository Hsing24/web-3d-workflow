# Web 3D Workflow

以 AI 自主製作為主的網站 3D 工作流。依產出目標選擇前置素材、建模與生成方式，再以條件式加工、視覺審查及網站量測完成交付。

目前提供可讀取使用的 skill、製作需求模板、路線矩陣、工具選擇與品質關卡。生成服務的串接與各路線的製作能力，依[樣本驗證計畫](docs/validation-plan.md)逐項驗證後，再加入可重複使用的腳本。

## 文件入口

| 文件 | 用途 |
| --- | --- |
| [Skill](skills/web-3d-workflow/SKILL.md) | Agent 的執行入口與共用規則 |
| [路線矩陣](skills/web-3d-workflow/references/routes.md) | 依目標選擇素材、路線與動態分支 |
| [工具選擇](skills/web-3d-workflow/references/tooling.md) | 確認能力、版本、服務與實際可呼叫介面 |
| [品質關卡](skills/web-3d-workflow/references/quality-gates.md) | 定義每階段的證據與失敗處理 |
| [製作需求模板](skills/web-3d-workflow/assets/production-brief.yaml) | 建立個別模型的需求與預算 |
| [樣本驗證計畫](docs/validation-plan.md) | 驗證 skill 決策與實際工具鏈的次序 |

## 使用方式

在 Agent 中指定讀取本目錄的 `skills/web-3d-workflow/SKILL.md`。例如：

> 使用此路徑的 web-3d-workflow skill，替網站規劃一個可旋轉展示的產品模型。先整理需要的素材、製作路線、最小樣本和驗收方式。

此目錄保存 skill 原始碼；是否能以 `$web-3d-workflow` 自動發現，取決於 Agent 的技能安裝與搜尋設定。讀取絕對路徑即可使用文件指引。

## 製作流程

需求與品質參考 → 路線與素材檢查 → 最小可行樣本 → 形體與動態驗證 → 必要加工 → 網站輸出 → 視覺與效能驗收。

每件資產保留可編輯來源、網站版本與驗收證據。出現缺陷時回到相應階段；預算或方法達到限制時，改換來源、工具或製作策略。

## 範圍

工作流涵蓋程序與 CAD 建模、影像轉 3D、既有基底改作、掃描、分件互動、角色變形及程序視覺。工具依需求選用；Blender 作為主要加工環境，MCP 與 CLI 均可作為操作介面。

本階段整理通用方法。個別模型的風格、動作與品質目標，在其製作需求中另行定義。
