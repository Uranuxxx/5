def calculate_change(total_amount, purchase_amount):
    coins = {
        500: 0, 
        100: 0, 
        50: 0, 
        10: 0 
    }

    change = total_amount - purchase_amount
    if change < 0:
        print("投入金額が足りません。")
        return

    for coin in coins.keys():
        coins[coin], change = divmod(change, coin)

    print(f"おつり: {total_amount - purchase_amount}円")
    for coin, count in coins.items():
        if count > 0:
            print(f"{coin}円硬貨: {count}枚")


if __name__ == "__main__":
    try:
        total_amount = int(input("投入金額を入力してください（円）: "))
        purchase_amount = int(input("商品の金額を入力してください（円）: "))

        calculate_change(total_amount, purchase_amount)
    except ValueError:
        print("無効な入力です。数値を入力してください。")
