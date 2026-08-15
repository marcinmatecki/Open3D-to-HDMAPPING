# Open3D point-cloud registration simplified instruction

## Step 1 (prepare data)

Download the KITTI sequence 00 dataset from [kitti_to_ros](https://github.com/Jakubach/kitti_to_ros).

In the **SeqLiDAR + IMUCalibration** section download:

- 2011_10_03_drive_0027_extract.zip
- 
Extract the dataset:

```shell
unzip 2011_10_03_drive_0027_extract.zip
```

After extraction, the folder `2011_10_03_drive_0027_extract` should be located in:

```text
~/hdmapping-benchmark-loop-closure/data
```

The point clouds should be located in:

```text
~/hdmapping-benchmark-loop-closure/data/2011_10_03_drive_0027_extract/velodyne_points/data
```

---

## Step 2 (prepare docker)

Run following commands in terminal:

```shell
mkdir -p ~/hdmapping-benchmark-loop-closure
cd ~/hdmapping-benchmark-loop-closure
git clone https://github.com/marcinmatecki/OPEN3D --recursive
cd benchmark-HDMapping-AILoopClosure-Open3D
docker build -t open3d_docker .
```

---

## Step 3 (run docker)

Make the script executable:

```shell
cd ~/hdmapping-benchmark-loop-closure/benchmark-HDMapping-AILoopClosure-Open3D
chmod +x docker_session_run-open3d.sh
```

Run Open3D using the KITTI LiDAR data:

```shell
./docker_session_run-open3d.sh ~/hdmapping-benchmark-loop-closure/data/2011_10_03_drive_0027_extract/velodyne_points/data
```

The script uses the selected folder as `/data` inside the Docker container.

The first point clouds used by Open3D are:

```text
/data/0000000000.txt
/data/0000000001.txt
```

---

## Step 4 (Open3D processing)

Open3D performs point-cloud registration processing on the selected LiDAR scans.

The input directory contains:

```text
0000000000.txt
0000000001.txt
0000000002.txt
...
```

The processing is performed automatically after starting the Docker container.
