
# Real-Time ArcFace Multiplex Recognition

## How to run

* Install yarn
  * `sudo apt install curl`
  * `curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -`
  * `echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list`
  * `sudo apt update && sudo apt install yarn`
* Electron Node-JS Client
  * `cd electron-client`
  * `yarn` or `npm install`
  * `yarn start` or `npm start`
* Build R-CNN for Retina Face
  * `cd ..`
  * `chmod a+x ./build_darknet_and_rcnn.sh`
  * `./build_rcnn.sh`
* Python Deal
  * `python3 usb_camera.py -c X` e.g: Replace X with 0
  * Click the corresponding `Camera {X}` Button at Electron
* Result (Nearly 24 fps at GTX1660ti)
  ![ArcFace Demo](./Media/result.png)

## How to train mlp classifier

* `mkdir ./Temp/raw`
* `mkdir ./Temp/train_data`
* Place training pictures in the following format：

    ```shell
    ─── train_data
        ├── bush
        │   ├── 1559637960.1595788.jpg
        │   ├── 1559637960.1762984.jpg
        │   └── 1559637960.2001894.jpg
        ├── clinton
        │   ├── 1559637960.2104468.jpg
        │   ├── 1559637960.2225769.jpg
        │   └── 1559637960.281161.jpg
        └── obama
            ├── 1559637960.2940397.jpg
            ├── 1559637960.31212.jpg
            └── 1559637960.3381834.jpg
    ```

* `python3 train_mlp.py`

## Citation

If you find *InsightFace* useful in your research, please consider to cite the following related papers:

```
@inproceedings{deng2019retinaface,
    title={RetinaFace: Single-stage Dense Face Localisation in the Wild},
    author={Deng, Jiankang and Guo, Jia and Yuxiang, Zhou and Jinke Yu and Irene Kotsia and Zafeiriou, Stefanos},
    booktitle={arxiv},
    year={2019}
}

@inproceedings{deng2018arcface,
    title={ArcFace: Additive Angular Margin Loss for Deep Face Recognition},
    author={Deng, Jiankang and Guo, Jia and Niannan, Xue and Zafeiriou, Stefanos},
    booktitle={CVPR},
    year={2019}
}
```
