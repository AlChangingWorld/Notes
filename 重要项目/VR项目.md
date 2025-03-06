
## 网络通信 NetCode
添加组件 NetworkManager
在NetworkManager组件中 将事先准备好的预制体拖入
Unity Netcode 用于网络通信，Unity Relay 服务用于低延迟连接，以及相关的 UI 组件用于玩家交互

在游戏启动时，LobbyUI.cs负责初始化 UI 元素，并为按钮添加点击事件监听器
UIEnabler方法用于切换不同的 UI 界面，按钮点击事件会触发相应的大厅操作（如快速加入、创建大厅等）。
当玩家点击创建大厅按钮后，LobbyManager.cs中的CreateLobby方法会被调用
配置创建大厅的选项，然后调用RelayManager创建 Relay 游戏并获取加入代码，将加入代码和游戏模式存储在大厅数据中，最后创建大厅
RelayManager.cs中的CreateRelayGame方法负责创建 Relay 游戏
此方法会创建 Relay 分配，获取加入代码，设置 Relay 连接数据，并启动主机

另一个玩家可以通过点击快速加入按钮或查看大厅列表并选择加入某个大厅。LobbyManager.cs中的JoinLobby方法会被调用。
然后加入指定 ID 的大厅，获取大厅中的 Relay 加入代码，最后调用RelayManager加入 Relay 游戏。

## 物体同步
具有网络行为的物体都要加上Network Object组件
如果想要同步位置会进行动态改变的物体，那么就要添加Network Transform。

1. **服务器权威**
服务器作为数据计算的中心，并且执行相关逻辑。然后将信息同步给所有客户端，提供了一个相对公平的游戏环境；

unity默认使用服务器权威，对应使用NetworkTransform;

优点:防止作弊，对于玩家来说作弊难度大
缺点;延迟高，用户体验感不好

2. 客户端权威
客户端权威是在本地进行数据的计算并且完成本地玩家的移动，然后本地将同步信息发送给服务器端，服务器端根据发送过来的消息将服务器自身的这个玩家进行信息同步，然后服务器端将信息发送给其他客户端，让其他客户端去同步这个玩家的信息；
使用客户端权威,对应使用ClientNetworkTransform

优点:用户体验感好
缺点:容易作弊
unity里没有ClientNetworkTransfoem组件, 需要自己添加;


