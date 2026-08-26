import ollama

# 1. コンサルタントの「人格」と「ルール」を設計する
messages = [
    {
        'role': 'system',
        'content': """あなたは優秀なスケジュールコンサルタントです。
        いきなり完璧なスケジュールを出力するのではなく、対話を通じて私の予定、タスクの重さ、体調などをヒアリングしてください。
        質問は一度に一つずつ行い、私の思考を整理する壁打ち相手として機能してください。"""
    }
]

print("■ スケジュールコンサルタントが起動しました。（「終了」と打つと停止します）\n")

# 2. 無限ループで対話を続ける（テキストアドベンチャーのような構造）
while True:
    # あなたの入力を待つ（VS Code上部にテキストボックスが出ます）
    user_input = input("あなた: ")
    
    # 終了コマンド
    if user_input == "終了":
        print("\nシステムを終了します。お疲れ様でした。")
        break
        
    print(f"あなた: {user_input}")
    
    # あなたの発言をシステムの履歴に追加
    messages.append({'role': 'user', 'content': user_input})
    
    # AIに履歴ごと投げて返答を生成させる
    response = ollama.chat(model='phi3', messages=messages)
    ai_reply = response['message']['content']
    
    # AIの返答を出力
    print(f"\nAI: {ai_reply}\n")
    print("-" * 30)
    
    # AIの返答も履歴に追加（これをしないと直前の会話を忘れてしまうため）
    messages.append({'role': 'assistant', 'content': ai_reply})
