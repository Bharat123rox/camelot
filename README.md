<p align="center">
   <img src="https://raw.githubusercontent.com/socialcopsdev/camelot/master/docs/_static/camelot.png" width="200">
</p>

# Camelot: PDF Table Extraction for Humans

[![Build Status](https://travis-ci.org/socialcopsdev/camelot.svg?branch=master)](https://travis-ci.org/socialcopsdev/camelot) [![Documentation Status](https://readthedocs.org/projects/camelot-py/badge/?version=master)](https://camelot-py.readthedocs.io/en/master/)
 [![codecov.io](https://codecov.io/github/socialcopsdev/camelot/badge.svg?branch=master&service=github)](https://codecov.io/github/socialcopsdev/camelot?branch=master)
 [![image](https://img.shields.io/pypi/v/camelot-py.svg)](https://pypi.org/project/camelot-py/) [![image](https://img.shields.io/pypi/l/camelot-py.svg)](https://pypi.org/project/camelot-py/) [![image](https://img.shields.io/pypi/pyversions/camelot-py.svg)](https://pypi.org/project/camelot-py/) [![Gitter chat](https://badges.gitter.im/camelot-dev/Lobby.png)](https://gitter.im/camelot-dev/Lobby)

**Camelot** is a Python library that makes it easy for *anyone* to extract tables from PDF files!

**Note:** You can also check out [Excalibur](https://github.com/camelot-dev/excalibur), which is a web interface for Camelot!

---

**Here's how you can extract tables from PDF files.** Check out the PDF used in this example [here](https://github.com/socialcopsdev/camelot/blob/master/docs/_static/pdf/foo.pdf).

```python3
>>> import camelot
>>> tables = camelot.read_pdf('foo.pdf')
>>> tables
<TableList n=1>
>>> tables.export('foo.csv', f='csv', compress=True) # json, excel, html, sqlite
>>> tables[0]
<Table shape=(7, 7)>
>>> tables[0].parsing_report
{
    'accuracy': 99.02,
    'whitespace': 12.24,
    'order': 1,
    'page': 1
}
>>> tables[0].to_csv('foo.csv') # to_json, to_excel, to_html, to_sqlite
>>> tables[0].df # get a pandas DataFrame!
```

| Cycle Name | KI (1/km) | Distance (mi) | Percent Fuel Savings |                 |                 |                |
|------------|-----------|---------------|----------------------|-----------------|-----------------|----------------|
|            |           |               | Improved Speed       | Decreased Accel | Eliminate Stops | Decreased Idle |
| 2012_2     | 3.30      | 1.3           | 5.9%                 | 9.5%            | 29.2%           | 17.4%          |
| 2145_1     | 0.68      | 11.2          | 2.4%                 | 0.1%            | 9.5%            | 2.7%           |
| 4234_1     | 0.59      | 58.7          | 8.5%                 | 1.3%            | 8.5%            | 3.3%           |
| 2032_2     | 0.17      | 57.8          | 21.7%                | 0.3%            | 2.7%            | 1.2%           |
| 4171_1     | 0.07      | 173.9         | 58.1%                | 1.6%            | 2.1%            | 0.5%           |

There's a [command-line interface](https://camelot-py.readthedocs.io/en/master/user/cli.html) too!

Refer to the [QuickStart Guide](https://github.com/socialcopsdev/camelot/blob/master/docs/user/quickstart.rst#quickstart) to quickly get started with Camelot, extract tables from PDFs and explore some basic options.

**Note:** Camelot only works with text-based PDFs and not scanned documents. (As Tabula [explains](https://github.com/tabulapdf/tabula#why-tabula), "If you can click and drag to select text in your table in a PDF viewer, then your PDF is text-based".)

## Why Camelot?

- **You are in control.**: Unlike other libraries and tools which either give a nice output or fail miserably (with no in-between), Camelot gives you the power to tweak table extraction. (This is important since everything in the real world, including PDF table extraction, is fuzzy.)
- *Bad* tables can be discarded based on **metrics** like accuracy and whitespace, without ever having to manually look at each table.
- Each table is a **pandas DataFrame**, which seamlessly integrates into [ETL and data analysis workflows](https://gist.github.com/vinayak-mehta/e5949f7c2410a0e12f25d3682dc9e873).
- **Export** to multiple formats, including JSON, Excel, HTML and Sqlite.

See [comparison with other PDF table extraction libraries and tools](https://github.com/socialcopsdev/camelot/wiki/Comparison-with-other-PDF-Table-Extraction-libraries-and-tools).

## Installation

### Using conda

The easiest way to install Camelot is to install it with [conda](https://conda.io/docs/), which is a package manager and  environment management system for the [Anaconda](http://docs.continuum.io/anaconda/) distribution.

```bash
conda install -c conda-forge camelot-py
```

### Using pip

After [installing the dependencies](https://camelot-py.readthedocs.io/en/master/user/install-deps.html) ([tk](https://packages.ubuntu.com/trusty/python-tk) and [ghostscript](https://www.ghostscript.com/)), you can simply use pip to install Camelot:

```bash
pip install camelot-py[cv]
```

### From the source code

After [installing the dependencies](https://camelot-py.readthedocs.io/en/master/user/install.html#using-pip), clone the repo using:

```bash
git clone https://www.github.com/socialcopsdev/camelot
```

and install Camelot using pip:

```
cd camelot
pip install ".[cv]"
```

## Documentation

Great documentation is available at [http://camelot-py.readthedocs.io/](http://camelot-py.readthedocs.io/).

## Development

The [Contributor's Guide](https://camelot-py.readthedocs.io/en/master/dev/contributing.html) has detailed information about contributing code, documentation, tests and more. We've included some basic information in this README.

### Source code

You can check the latest sources with:

```bash
git clone https://www.github.com/socialcopsdev/camelot
```

### Setting up a development environment

You can install the development dependencies easily, using pip:

```bash
pip install camelot-py[dev]
```

### Testing

After installation, you can run tests using:

```bash
python setup.py test
```

## Versioning

Camelot uses [Semantic Versioning](https://semver.org/). For the available versions, see the tags on this repository. For the changelog, you can check out [HISTORY.md](https://github.com/socialcopsdev/camelot/blob/master/HISTORY.md).

## License

This project is licensed under the MIT License, see the [LICENSE](https://github.com/socialcopsdev/camelot/blob/master/LICENSE) file for details.
