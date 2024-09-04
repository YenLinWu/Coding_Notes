# VS Code 中建立虛擬環境
- 選擇 Python 版本  
Step 1: 輸入 Ctrl + Shift + P  
Step 2: 輸入 Python: Select Interpreter   
Step 3: 選擇 Python 版本    

- 建立 Python 虛擬環境
  ```console
  python -m venv env_name
  ```

- 啟動虛擬環境
  ```console
  env_name/scripts/activate
  ```

- 安裝 Python 套件
  ```console
  pip install -r requirements.txt
  ```

- 顯示套件版本
  ```console
  pip list
  ```

## 其他資源
- [Python 安裝檔](https://www.python.org/downloads/windows/)
- [Python environments in VS Code](https://code.visualstudio.com/docs/python/environments)
