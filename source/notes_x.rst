Stuff And Things
=================

Here's some python code::

    import sys
    import pandas as pd


    def main():
        df = pd.read_csv(sys.argv[1])
        print df.head(2).T

    if __name__ == '__main__':
        main()

The end.
