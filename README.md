import traceback

def safe_calculate_decorator(func):
    def wrapper(expression):
        try:
            result = func(expression)
            return result
        except Exception as e:
            error_message = f"oshibka pri bichislenii '{expression}': {str(e)}"
            print(error_message)
            print("podrobrosti oshibki:")
            traceback.print_exc()
            return None
    return wrapper

@safe_calculate_decorator
def calculate(expression):
    return eval(expression)
    
print(calculate("5 + 3"))
print(calculate("10 / 0"))  
print(calculate("nepravilno"))  
