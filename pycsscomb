#!/usr/bin/env python
import os
import sys
import argparse
import subprocess


def toTmpFile(start, end, file):
    filename, file_extension = os.path.splitext(file)
    currentDir = os.path.dirname(os.path.realpath(__file__))
    tempfile = "%s/tmpfile%s" % (currentDir, file_extension)
    with open(file) as f:
        lines = [l for i, l in enumerate(f) if i >= start-1 and i < end]
        with open(tempfile, "w") as f1:
            f1.writelines(lines)
    return tempfile


def removeLines(fileName, start, end):
    """Remove lines from start ot end"""
    tempFile = open(fileName)
    tempList = []
    for lineNum, line in enumerate(tempFile):
        if lineNum >= start-1 and lineNum < end:
            continue  # do next lineNum, line without append()
        tempList.append(line)
    tempFile.close()
    tempFile = open(fileName, 'w')
    tempFile.writelines(tempList)
    tempFile.close()


def returnStyle(fromFile, toFile, fromRow):
    f = open(toFile, "r")
    toFileContents = f.readlines()
    f.close()

    count = fromRow
    f = open(fromFile, "r")
    fromFileContents = f.readlines()

    for value in fromFileContents:
        toFileContents.insert(count, value)
        count += 1

    f = open(toFile, "w")
    contents = "".join(toFileContents)
    f.write(contents)
    f.close()


def runCSSComb(file):
    subprocess.check_call("csscomb %s" % file, shell=True)


def main(args):
    tempfile = toTmpFile(args.start, args.end, args.file)
    removeLines(args.file, args.start, args.end)
    runCSSComb(tempfile)
    returnStyle(tempfile, args.file, args.start-1)


if __name__ == '__main__':
    parser = argparse.ArgumentParser()
    parser.add_argument('-s', '--start', type=int, default=False)
    parser.add_argument('-e', '--end', type=int, default=False)
    parser.add_argument('-f', '--file', type=str, default=False)

    args = parser.parse_args()

    main(args)
