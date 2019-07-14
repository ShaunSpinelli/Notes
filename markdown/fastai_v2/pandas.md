# Pandas

[Pandas in 10min](https://pandas.pydata.org/pandas-docs/stable/10min.html)

## Object Creation

## Viewing data

## Selecting Data



## from lesson 3

```python
data.classes
```

Displays test file name

```python
data.test_ds.fnames
```

Predictions returned as log so need to unlog them to get probablities

```python
log_preds,y = leran.TTA(is_test=True)
probs = np.exp(log_preds)
```
matrix of (files,classes)

```python
probs.shape
```

Use pandas to write the text file

```python
df = pd.DataFrame(probs)
df.columns = data.classes
```

```python
df.insert(0, 'id',[o for o in data.test_ds.fnames])
```
view data fram

```python
df.head()
```

Create file

```python
SUBM = f'{PATH}subm'
os.makedirs(SUBM, exist_ok=True)
df.to_csv(f'{SUBM}subm.gz', compression='gzip',index=False)
```
Gives link for you to click and download folder

```python
FileLink(f'{SUBM}subm.gz')
```

