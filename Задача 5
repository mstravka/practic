import sys
from datetime import datetime

class Formatter:
    def format(self, message):
        raise NotImplementedError

class TimeFormatter(Formatter):
    def __init__(self, time_format='%Y-%m-%d %H:%M:%S'):
        self.time_format = time_format

    def format(self, message):
        timestamp = datetime.now().strftime(self.time_format)
        return f"[{timestamp}] {message}"

class Handler:
    def handle(self, formatted_message):
        raise NotImplementedError

class StderrHandler(Handler):
    def handle(self, formatted_message):
        print(formatted_message, file=sys.stderr)

class Logger:
    def __init__(self, formatter: Formatter):
        self.formatter = formatter
        self.handlers = []

    def add_handler(self, handler: Handler):
        self.handlers.append(handler)

    def log(self, message):
        formatted = self.formatter.format(message)
        for handler in self.handlers:
            handler.handle(formatted)

if __name__ == '__main__':
    formatter = TimeFormatter('%Y-%m-%d %H:%M:%S')
    logger = Logger(formatter)

    stderr_handler = StderrHandler()
    logger.add_handler(stderr_handler)

    logger.log('Logging with Strategy and Observer')
