# Saving and loading a model in `pytorch`
> 30/05/2017

#### To save a model at some checkpoint, call the following function :
```python
def save_checkpoint(state, is_best, filename='checkpoint.pth.tar'):
    torch.save(state, filename)
    if is_best:
        shutil.copyfile(filename, 'model_best.pth.tar')
```
  - `state` must be a python dict
  - if current model is the best one, set `is_best` arg as `True`, else `False`
  - Example call:
    ```python
    save_checkpoint({
            'epoch': 1,
            'state_dict': model.state_dict(),
            'optimizer' : optimizer.state_dict(),
        }, True)
    ```
  
