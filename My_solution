#include <bits/stdc++.h>
#define pb push_back
#define pii pair<int, int>
#define S second
#define F first
using namespace std;
const int MAXN = 100005;
typedef long long ll;

pair<int, pii> p[50004];
vector<int> l, r;
int pre[50004], suf[50004];
int main() {
    freopen("meetings.in", "r", stdin);
    freopen("meetings.out", "w", stdout);
    int n, L, W = 0;
    cin>>n>>L;
    for(int i=0;i<n;i++){
        cin>>p[i].S.F>>p[i].F>>p[i].S.S;
        W += p[i].S.F;
    }
    sort(p, p+n);
    pre[0] = p[0].S.F;
    suf[0] = p[n-1].S.F;
    for(int i=0;i<n;i++){
//        if(i){
//            pre[i] = pre[i-1] + p[i].S.F;
//        }
        if(p[i].S.S == 1){
            r.pb(i);
        }
        else{
            l.pb(i);
        }
    }
    reverse(r.begin(), r.end());
//    for(int i=n-2;i>=0;i--){
//        suf[n-i-1] = suf[n-i-2] + p[i].S.F;
//    }
    int p1 = 0, p2 = 0;
    int sum = 0;
    while(p1 < l.size() && p2 < r.size() && sum*2 < W){
        int ind1 = l[p1], ind2 = r[p2];
        if(p[ind1].F < (L - p[ind2].F)){
            sum += p[p1].S.F;
            p1++;
            continue;
        }
        if(p[ind1].F > (L - p[ind2].F)){
            sum += p[n-1-p2].S.F;
            p2++;
            continue;
        }
        if(p[ind1].F == (L - p[ind2].F)){
            sum += p[p1].S.F;
            p1++;
            sum += p[n-1-p2].S.F;
            p2++;
            continue;
        }
    }
    while(p1 < l.size() && sum*2 < W){
        sum += p[p1].S.F;
        p1++;
    }
    while(p2 < r.size() && sum*2 < W){
        sum += p[n-1-p2].S.F;
        p2++;
    }

    int dis = 0;
    if(p1){
        dis = max(dis, p[l[p1-1]].F);
    }
    if(p2){
        dis = max(dis, L - p[r[p2-1]].F);
    }
    ll res = 0;
    for(auto x : r){
        int lef = 0, ri = l.size();
        int from = -1;
        while(lef < ri){
            int mid = (lef + ri) / 2;
            if(p[l[mid]].F - p[x].F < 0){
                lef = mid+1;
                from = mid;
            }
            else{
                ri = mid;
            }
        }
        lef = 0, ri = l.size();
        int to = -1;
        while(lef < ri){
            int mid = (lef + ri) / 2;
            if(p[l[mid]].F - p[x].F > dis*2){
                ri = mid;
            }
            else{
                lef = mid+1;
                to = mid;
            }
        }
        if(to == -1)continue;
        res += to - from;
    }
    cout<<res;
    return 0;
}

