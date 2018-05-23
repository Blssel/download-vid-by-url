# 下载youtube上的数据集（youtube-dl工具）

现在许多动作识别数据集，涉及到的数据量巨大，而且由于版权的缘故，往往仅提供视频的URL，这就要求我们自己下载，下面的工具可以依据URL下载视频，目前仅限youtube上的视频

所有文件都在download-vid-by-url文件夹中，其中download.py文件是主文件，运行它可以启动下载，目前仅提供activitynet和kinetics数据集的下载（持续更新），其实操作方式大同小异，具体操作方式是如下：

## 准备包含视频ID和URL的文件

最终视频的存放方式是：以视频ID为视频名，拓展名为.mp4，所有视频都存放在同一个文件夹下，不区分类别。比如activitynet和kinetics数据集是以.json文件方式提供ID和URL。

## 运行download.py文件
```shell
cd download
python download.py --dataset DATASET_NAME JSON_PATH FAILED_PATH --num_thread NUM_THREAD 
```
视频就保存在download.py所在文件夹。其中，DATASET_NAME, JSON_PATH，FAILED_PATH和NUM_THREAD分别表示所下载的数据集名称(在activity_net kinetics ava中选择)，json文件的存放位置，下载失败信息的保存位置，线程数(根据电脑配置和网络情况酌情选择，我设置在100左右)。

比如
```shell
python download.py --dataset kinetics ../kinetics_url/kinetics_400/kinetics_train/kinetics_train.json kinetics_train_failed.txt --num_thread 100
# 或者
python download.py --dataset activity_net ../activitynet_url/activity_net.v1-3.min.json activity_test_failed.txt --num_thread 10
```

