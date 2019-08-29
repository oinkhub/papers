size at zoom 13: 163840
size at zoom 16: 20480
size at zoom 19: 2560
size at zoom 20: 1280

original image size: 256
size of world: 268435456
world / 256 = 1048576





# zoom 13
tile size: 32768


2^13 = 8192
(world size) / (2^zoom) = tile size
268435456 / (2^13) = 32768
268435456 / 8192 = 32768

world size = tile size * (2^zoom)
world size / tile size = 2 ^ zoom


256*8 = 2048
268435456 / 2048 = 131072 = 2 ^ 17

256 * 4 = 1024
268435456 / 1024 = 262144 = 2 ^ 18

# using image size of 2048, from hubraum to alexanderplatz, only scale 17 (max)
mapping about 5 minutes
result 362,7 MB

using zoom 16: 228,8



268435456 / 1024 = 262144 = 2 ^ 18

2^17 = 131072
2^16 = 65536

x * tile_size / wanted_tile_size


