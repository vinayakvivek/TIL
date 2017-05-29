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
  - Example call :
  
    ```python
    save_checkpoint({
            'epoch': 1,
            'state_dict': model.state_dict(),
            'optimizer' : optimizer.state_dict(),
        }, True)
    ```
 
#### To load a trained model, use `torch.load()`
  - Example :
  
    ```python
    # initialize model, `UNet` is my custom model
    model = UNet().cuda()
    model = torch.nn.DataParallel(model, device_ids=[0, 1])

    # initialize optimizer
    optimizer = optim.Adam(model.parameters(), lr=1e-4, weight_decay=5e-5)

    # load checkpoint
    checkpoint = torch.load('checkpoint.pth.tar')

    # load the saved state into initialized model and optimizer
    model.load_state_dict(checkpoint['state_dict'])
    optimizer.load_state_dict(checkpoint['optimizer'])
    ```

