# Deep Residual Network using `PyTorch`
> 08/06/2017

```python
class ResBlock(nn.Module):
    
    def __init__(self):
        super(ResBlock, self).__init__()
        self.conv1 = nn.Conv2d(128, 32, 3, padding=1)
        self.bn1 = nn.BatchNorm2d(32)
        self.conv2 = nn.Conv2d(32, 32, 3, padding=1)
        self.bn2 = nn.BatchNorm2d(32)
        self.conv3 = nn.Conv2d(32, 128, 3, padding=1)
        
    def forward(self, x):
        _x = x
        x = F.relu(self.bn1(self.conv1(x)))
        x = F.relu(self.bn2(self.conv2(x)))
        x = self.conv3(x)
        x += _x
        return x



class ResNet(nn.Module):
    
    def __init__(self):
        super(ResNet, self).__init__()
        self.conv1 = nn.Conv2d(3, 128, 3, padding=1)
        self.bn1 = nn.BatchNorm2d(128)
        self.res_block1 = ResBlock()
        self.res_block2 = ResBlock()
        self.res_block3 = ResBlock()
        self.res_block4 = ResBlock()
        self.res_block5 = ResBlock()
        self.bn2 = nn.BatchNorm2d(128)
        self.avg_pool = nn.AvgPool2d(16)
        self.fc = nn.Linear(128, 10)
        
    def forward(self, x):
        x = F.max_pool2d(self.conv1(x), 2)
        x = F.relu(self.bn1(x))
        x = self.res_block1(x)
        x = self.res_block2(x)
        x = self.res_block3(x)
        x = self.res_block4(x)
        x = self.res_block5(x)
        x = F.relu(self.bn2(x))
        x = self.avg_pool(x)
        x = x.view(-1, 128)
        x = self.fc(x)
        return x
```

 - this ResNet achieved ~82 % accuracy on `CIFAR-10` test dataset. 
