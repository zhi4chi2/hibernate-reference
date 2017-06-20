javax.persistence.CascadeType 同名
- ALL
- PERSIST
- MERGE
- REMOVE
- REFRESH
- DETACH


在 javax.persistence.CascadeType 之外额外定义
- DELETE
- SAVE_UPDATE
- REPLICATE
- LOCK


另有两个已经作废
- DELETE_ORPHAN - 使用 @OneToOne(orphanRemoval=true) or @OneToMany(orphanRemoval=true)
- EVICT - 使用 DETACH
