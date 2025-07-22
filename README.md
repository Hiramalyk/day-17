# day-17
import logging, unittest

logging.basicConfig(filename='error_log.txt', level=logging.ERROR,
                    format='%(asctime)s - %(levelname)s - %(message)s')

class DivisionByZeroError(Exception): pass

def add(x, y): return x + y
def subtract(x, y): return x - y
def multiply(x, y): return x * y
def divide(x, y):
    if y == 0:
        logging.error("Divide by zero")
        raise DivisionByZeroError("Cannot divide by zero.")
    return x / y

class TestCalc(unittest.TestCase):
    def test_ops(self):
        self.assertEqual(add(1,2),3)
        self.assertEqual(subtract(5,2),3)
        self.assertEqual(multiply(2,3),6)
        self.assertEqual(divide(10,2),5)
        with self.assertRaises(DivisionByZeroError):
            divide(1, 0)

if __name__ == "__main__":
    unittest.main()
