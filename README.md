## 内容

| 打刻画面（メインUI） | 日次・月次集計グラフ |
|----------------|------------------|
| ![punch](https://raw.githubusercontent.com/mikan202510/django-attendance-system/main/hrm_py/hrm_py/django-attendance-system1.jpeg) | ![summary](https://raw.githubusercontent.com/mikan202510/django-attendance-system/main/hrm_py/hrm_py/django-attendance-system2.jpeg) |

| 月次データ一覧 | チーム集計（管理者向け） |
|----------------|----------------|
| ![monthly](https://raw.githubusercontent.com/mikan202510/django-attendance-system/main/hrm_py/hrm_py/django-attendance-system3.jpeg) | ![team](https://raw.githubusercontent.com/mikan202510/django-attendance-system/main/hrm_py/hrm_py/django-attendance-system4.jpeg) |

| 残業・休暇申請画面 |
|----------------|
| ![request](https://raw.githubusercontent.com/mikan202510/django-attendance-system/main/hrm_py/hrm_py/django-attendance-system5.jpeg) |

# Django × Streamlit 勤怠管理システム ― 打刻と集計の可視化アプリ
- Django REST Framework と Streamlit を組み合わせた、勤怠打刻と勤務時間集計を自動化・可視化するWebアプリです
- 出勤・退勤・休憩の打刻API、日次／週次／月次の勤怠集計、グラフ表示を実装
- ローカル開発環境で実行可能なポートフォリオ・学習用プロジェクトです

---

## 開発の目的 
 
- 「勤怠データの記録・集計・可視化」を一連の仕組みとして自作し、フロントとバックエンドの連携設計・API構築・データ可視化の理解を深めることを目的としました
- バックエンド（Django）とフロントエンド（Streamlit）の統合構成を実践的に学習

---

## 使用技術 

- Backend：Django / Django REST Framework / SimpleJWT / CORS Headers
- Frontend：Streamlit / Altair / Pandas / Requests  
- その他：python-dotenv / jpholiday / SQLite3
- 開発環境：Windows 10 / Python 3.11

---

## 機能 

- 出勤／退勤／休憩の打刻API（POST）
- 日次・週次・月次の勤怠集計API（GET）
- Streamlit UI（ボタン打刻・集計結果の可視化） 
- 社員別の勤務時間・残業時間・休暇日数の可視化
- JWT認証によるユーザー管理（開発モード対応）

---

## 工夫した点 

- Django REST Framework を用いてシンプルかつ拡張性のあるAPI設計を構築 
- Streamlit と Altair によるリアルタイム集計グラフ表示
- 祝日ライブラリ（jpholiday）で自動的に休日を判定  
- コードとUIを極力シンプルに保ち、学習用途にも理解しやすい構成に設計

---

## 実行方法 

- 1.ソースを取得
  
　　git clone https://github.com/mikan202510/Django-Attendance-System.git
  
　　cd Django-Attendance-System/hrm_py/hrm_py

- 2.仮想環境
  
　　python -m venv .venv
  
　　Windows
  
　　.\ .venv\Scripts\Activate.ps1

- 3.依存パッケージ
  
　　python -m pip install --upgrade pip
  
　　python -m pip install -r requirements.txt

- 4.環境ファイル
  
　　Windows PowerShell
  
　　if (!(Test-Path .env)) { New-Item -Name ".env" -ItemType "file" | Out-Null; Add-Content .env "DEBUG=True`nSECRET_KEY=django-insecure-　testkey`nALLOWED_HOSTS=127.0.0.1,localhost`nHRM_API_BASE=http://127.0.0.1:8000" }

- 5.データベース初期化 & テストユーザー

　　python manage.py migrate
  
　　python manage.py shell -c "from django.contrib.auth import get_user_model; U=get_user_model(); U.objects.filter(username='test@example.com').delete(); 　　　　　　U.objects.create_user(username='test@example.com', email='test@example.com', password='test1234')"

- 6.Djangoサーバー起動

　　python manage.py runserver 8000

- 7.別のターミナルで Streamlit（UI）を起動

　　cd Django-Attendance-System/hrm_py/hrm_py

- 8.仮想環境を有効化後

　　.\ .venv\Scripts\Activate.ps1
  
　　streamlit run app.py

　　ブラウザで勤怠システムの画面が開きます
  
　　もし自動で開かない場合は、ターミナルに表示されたURLをクリックしてください

---

## 想定利用シーン

- チームや個人の勤務時間を簡単に記録・可視化
- 小規模事業所の勤怠・残業・休暇の記録に利用

---

## 今後の展望 

- /api/hr/me の社員情報APIを実装し、Streamlitに表示
- 月次KPIグラフの拡張（平均残業時間・稼働率）
- Streamlit Cloud へのデモ公開

---

## 制作メモ

- 開発期間：約2日
- 開発環境：Windows 10 / Python 3.11 / Django 4.2 / Streamlit 1.36
